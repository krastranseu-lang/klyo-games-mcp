> **Strona kanoniczna:** https://games.klyo.pl/pl/wsparcie/zapis-postepu/ · aktualizacja 2026-11-10 · Plik powstaje automatycznie ze strony klyo games, więc poprawki wprowadzamy na stronie.

# Jak zapisać postęp gracza w grze HTML5

Dodaj zestaw klyo do index.html. Gra bez kodu zapisu i tak zachowa postęp: zestaw sam przenosi do chmury jej localStorage i pliki silnika. Gdy chcesz sam decydować, co jest postępem, wołaj klyo.save.get na starcie i klyo.save.set po ważnej zmianie. Postęp idzie za zalogowanym graczem na każde urządzenie.

- 4 min czytania
- Kroki: 5

### Na tej stronie

## Zanim zaczniesz

- Gra w przeglądarce (czysty JavaScript, Godot, Unity, GameMaker albo inny silnik z eksportem do przeglądarki) i dostęp do jej pliku index.html.
- Stan gry jako obiekt, który mieści się w 64 KB, na przykład poziom, monety i ustawienia.
- Po twojej stronie nie potrzeba serwera ani bazy danych: resztę robią zestaw i strona klyo.

## Krok po kroku

1. **Dodaj zestaw**: Wstaw tę linijkę do pliku index.html przed własnym skryptem: ``. Silnik z eksportem do przeglądarki woła te same funkcje swoim sposobem wywołania JavaScriptu: w Godot to `JavaScriptBridge`, w Unity wtyczka `.jslib`.
2. **Wczytaj postęp na starcie**: Wywołaj `klyo.save.get(odpowiedz)` raz, gdy gra startuje. Gdy `z.ok` jest prawdą, a `z.data` ma dane, odtwórz grę z `z.data`. `z.cloud` jest prawdą, gdy odpowiedział serwer klyo, a `z.reason` mówi, dlaczego dane są tylko z przeglądarki.
3. **Zapisuj po ważnych zmianach**: Wywołuj `klyo.save.set(stan, odpowiedz)` po poziomie, zakupie albo zmianie ustawień. Zestaw trzyma kopię w przeglądarce i łączy zapisy częstsze niż co 2 sekundy w jeden, więc nie potrzebujesz własnego licznika.
4. **Sprawdź w podglądzie w studiu**: Wgraj paczkę i zagraj w oknie podglądu. Zapis idzie do chmury podglądu, którą widzisz tylko ty, a odpowiedź ma `o.cloud` i `o.preview` równe prawdzie. Wywołaj `klyo.save.get` jeszcze raz albo otwórz podgląd ponownie: te same dane wracają z `z.source` równym "chmura".
5. **Wydaj grę**: Po wydaniu każdy gracz zapisuje we własnym miejscu: zalogowany ma postęp na każdym urządzeniu, gość w tej przeglądarce. Twój zapis z podglądu znika razem z podglądem.

## Jeśli coś nie działa

### Odpowiedź mówi, że dane są lokalne

`z.reason` mówi dlaczego. `bez-strony`: gra działa poza klyo (wprost z pliku albo na innej stronie), więc postęp zostaje w przeglądarce. `bez-serwera`: nie było połączenia, a zestaw wyśle kopię później. `pusto-w-chmurze`: w chmurze jeszcze nic nie było, więc gra dostała kopię z przeglądarki, a zestaw wysłał ją do chmury.

### Mój kod czeka, a potem się poddaje

Odpowiedź przychodzi zawsze, najpóźniej po 8 sekundach, a na klyo od razu. Usuń własny, krótszy limit czasu i uruchom grę z kopii w przeglądarce, zanim odpowie chmura.

### Zapis jest za duży

Odpowiedź ma `reason` równe `rozmiar`: stan po zakodowaniu ma więcej niż 64 KB. Zapisuj tylko to, czego trzeba do odtworzenia gry, a nie całą scenę.

### Bramka jakości w podglądzie mówi, że postęp nie przejdzie na inne urządzenia

Zestaw klyo nie jest pierwszym skryptem strony gry, więc kopia pamięci gry przychodzi, gdy gra już ją przeczytała. Przenieś linijkę zestawu nad wszystkie inne skrypty albo zapisuj postęp przez klyo.save.

## Czy gracz potrzebuje konta, żeby zachować postęp?

Nie. Bez konta postęp należy do tej przeglądarki. Z kontem idzie za graczem na każde urządzenie, a kopia zapisana w tej przeglądarce przed zalogowaniem przechodzi na konto.

## Co się dzieje, gdy dwa urządzenia zapisują naraz?

Wygrywa ostatni zapis w chmurze. Kopia z przeglądarki, której serwer jeszcze nie potwierdził, idzie do chmury tylko wtedy, gdy w międzyczasie nie zapisało inne urządzenie, więc starsza kopia nigdy nie nadpisze nowszego postępu.

## Czy gracze zobaczą moje testowe zapisy z podglądu?

Nie. Podgląd ma własne miejsce, które otwierasz tylko ty i moderatorzy klyo, i znika ono razem z podglądem.

## Czy localStorage wystarczy do zapisu gry w przeglądarce?

Na klyo tak. Zestaw sam kopiuje localStorage gry do chmury i wpisuje go na innym urządzeniu gracza, zanim gra ruszy, więc postęp przechodzi z telefonu na komputer bez jednej linijki kodu. Poza klyo zapis w localStorage zostaje w jednej przeglądarce i znika, gdy gracz wyczyści dane strony.

## Czy zapis z Godota albo Unity działa bez żadnego kodu?

Tak. Pliki zapisu silnika (Godot, Unity i inne silniki z eksportem do przeglądarki) leżą w bazie przeglądarki, a zestaw kopiuje je do chmury i wpisuje na nowym urządzeniu, zanim silnik je przeczyta. Zestaw musi być pierwszym skryptem strony gry; gdy paczka go nie ma, dokładamy go tam sami.

## Co, jeśli gracz ma inny postęp na dwóch urządzeniach?

Gracz wybiera. Nad grą pojawia się pasek z informacją, że na tym urządzeniu jest inny postęp niż na koncie, i z przyciskami **Wczytaj z konta** oraz **Zostaw ten**. Nic nie nadpisuje się po cichu.

## Jak duża może być pamięć gry?

Do 120 KB localStorage i 120 KB plików silnika na gracza i grę. Pojedynczy wpis większy niż 100 KB, na przykład obraz albo pamięć podręczna, i największe wpisy ponad ten budżet zostają tylko na urządzeniu. Gdy zapis przez klyo.save działa (serwer go potwierdził), zestaw tej kopii już nie robi: jeden zapis, jedna prawda.

## Czy zapis przetrwa nową wersję gry?

Tak. Zapis należy do adresu gry i do konta gracza, a nie do plików w paczce, więc nowa wersja dostaje ten sam zapis. Zanim ją wypuścisz, sprawdzisz to w podglądzie nowej wersji.

## Jak zapisać postęp z gry w Godot wydanej w przeglądarce?

Przez most silnika do JavaScriptu: gra dostaje obiekt zestawu klyo, a funkcja zwrotna odbiera odpowiedź. Pełny przykład kodu jest w dokumentacji zestawu.

## Jak wywołać zapis z Unity WebGL?

Z wtyczki JavaScript w projekcie: funkcja wtyczki woła zestaw klyo, a kod C# deklaruje tę funkcję i wywołuje ją jak każdą inną metodę.

## Powiązane instrukcje

- [Dokumentacja zapisu w zestawie klyo, z przykładem z Godota](https://games.klyo.pl/pl/zestaw-do-gry/#zapis)
- [Jak dodać tablicę wyników do gry HTML5](https://games.klyo.pl/pl/wsparcie/tablica-wynikow/)
- [Jak wydać grę HTML5 na klyo games](https://games.klyo.pl/pl/wsparcie/jak-wydac-gre-html5/)
- [Jak wydać nową wersję gry i wrócić do poprzedniej](https://games.klyo.pl/pl/wsparcie/nowa-wersja-gry/)
- [Wszystkie instrukcje](https://games.klyo.pl/pl/wsparcie/)

Nadal coś nie działa? Napisz na [kontakt@klyo.pl](mailto:kontakt@klyo.pl) i podaj adres gry. Odpowiada człowiek, w dwa dni robocze.

---

Źródło: https://games.klyo.pl/pl/wsparcie/zapis-postepu/ · Autor: klyo, polska firma technologiczna (Łódź, klienci w całej Polsce) · Kontakt: kontakt@klyo.pl · Indeks dla modeli językowych: https://games.klyo.pl/llms.txt
