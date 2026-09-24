> **Strona kanoniczna:** https://games.klyo.pl/pl/wsparcie/biale-okno/ · aktualizacja 2026-09-24 · Plik powstaje automatycznie ze strony klyo games, więc poprawki wprowadzamy na stronie.

# Gra pokazuje białe okno: jak to naprawić

Naciśnij „Pokaż, co się stało” w podglądzie studia. Zobaczysz pliki, o które gra prosiła i których nie dostała, oraz błędy, które rzuciła. Najczęściej winne są wielkie litery w nazwach plików, ścieżki bezwzględne albo skrypty z cudzego serwera.

## Zanim zaczniesz

- Gra jest wgrana do studia pod adresem dev.klyo.pl; wystarczy paczka, która czeka jeszcze na opis.
- Oryginalne pliki na twoim komputerze, żeby je poprawić i wgrać ponownie.

## Krok po kroku

1. **Otwórz diagnozę**: W podglądzie naciśnij **Pokaż, co się stało**. Zobaczysz brakujące pliki i błędy z przeglądarki w kolejności, w jakiej wystąpiły. Tę samą listę dostaje twój asystent AI z narzędzia diagnozy.
2. **Sprawdź nazwy plików litera po literze**: Nasz serwer rozróżnia wielkie litery: Player.png i player.png to dwa różne pliki. Gra działająca na Windowsie albo macOS może tu nie znaleźć plików, więc nazwy w kodzie muszą dokładnie zgadzać się z plikami.
3. **Używaj ścieżek względnych**: Wczytuj pliki jako assets/hero.png, a nie /assets/hero.png, C:\ czy file:///. Plik index.html trzymaj w głównym katalogu ZIP-a, nie w podfolderze.
4. **Trzymaj wszystko w paczce**: Gra na klyo wczytuje własne pliki. Biblioteka, krój pisma albo skrypt z cudzego serwera może się nie wczytać, a kod wysyłający dane poza klyo nie przechodzi sprawdzenia. Wrzuć taki plik do ZIP-a.
5. **Gry z silników eksportuj do ZIP-a**: GameMaker, Unity i Godot tworzą część nazw plików w trakcie działania gry, więc przeniesienie takiej gry z adresu może ich nie znaleźć. Wyeksportuj grę do ZIP-a w swoim silniku i wgraj cały folder.
6. **Przetestuj, zanim wgrasz ponownie**: Na swoim komputerze uruchom `node klyo-test.mjs http://localhost:8080/ moja-gra ./klyo-test`. Mierzy grę tak jak my przy wydaniu, z tymi samymi progami, i pokazuje, co zobaczy gracz.

## Jeśli coś nie działa

### Ekran długo zostaje pusty

Pierwsza klatka powinna pojawić się w 20 sekund, a pierwsze pobranie na telefonie zmieścić się w 20 MB. Duże pliki wczytuj później, gdy menu jest już na ekranie.

### Nie ma dźwięku

Przeglądarki włączają dźwięk dopiero po pierwszym dotknięciu albo kliknięciu. Wznawiaj dźwięk w geście gracza, także po powrocie gry z tła na iPhonie.

### Nic z listy tego nie wyjaśnia

Naciśnij **Porozmawiaj z nami** w studiu i wyślij adres gry ze zrzutem ekranu. Przeczyta to człowiek.

## Częste pytania

### Dlaczego gra działa u mnie, a na klyo nie?

Zwykle przez wielkie litery w nazwach plików, ścieżki bezwzględne albo pliki z cudzego serwera. Komputer lokalny to wybacza, serwer w sieci już nie.

### Czy asystent AI znajdzie przyczynę?

Tak. Podłączony przez serwer MCP klyo czyta tę samą diagnozę, brakujące pliki i błędy z przeglądarki, i może poprawić pliki w wersji roboczej, którą potem sam sprawdzasz i wydajesz.

## Powiązane instrukcje

- [Jak wydać grę HTML5 na klyo games](https://games.klyo.pl/pl/wsparcie/jak-wydac-gre-html5/)
- [Jak wydać nową wersję gry i wrócić do poprzedniej](https://games.klyo.pl/pl/wsparcie/nowa-wersja-gry/)
- [Jak dodać tablicę wyników do gry HTML5](https://games.klyo.pl/pl/wsparcie/tablica-wynikow/)
- [Wszystkie instrukcje](https://games.klyo.pl/pl/wsparcie/)

Nadal coś nie działa? Napisz na [kontakt@klyo.pl](mailto:kontakt@klyo.pl) i podaj adres gry. Odpowiada człowiek, w dwa dni robocze.

---

Źródło: https://games.klyo.pl/pl/wsparcie/biale-okno/ · Autor: klyo, polska firma technologiczna (Łódź, klienci w całej Polsce) · Kontakt: kontakt@klyo.pl · Indeks dla modeli językowych: https://games.klyo.pl/llms.txt
