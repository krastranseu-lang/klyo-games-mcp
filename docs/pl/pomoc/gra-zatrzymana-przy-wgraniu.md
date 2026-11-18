> **Strona kanoniczna:** https://games.klyo.pl/pl/wsparcie/gra-zatrzymana-przy-wgraniu/ · aktualizacja 2026-11-10 · Plik powstaje automatycznie ze strony klyo games, więc poprawki wprowadzamy na stronie.

# Dlaczego moja gra została zatrzymana przy wgraniu i jak to naprawić

Na klyo gra nic nie pobiera z cudzych serwerów i nic im nie wysyła, nie ma własnego logowania, a reklamy pokazuje tylko przez klyo. Pliki z publicznych CDN dokładamy do paczki sami. Na resztę karta w studiu podaje każdy powód, naprawę i polecenie dla Twojego AI.

- 2 min czytania
- Kroki: 6

### Na tej stronie

## Zanim zaczniesz

- Gra jest wgrana do studia pod adresem dev.klyo.pl, a podgląd pokazuje czerwoną kartę.
- Pliki gry na Twoim komputerze albo w narzędziu AI, żeby je zmienić i wgrać ponownie.

## Krok po kroku

1. **Przeczytaj kartę od góry**: Każdy ponumerowany wiersz mówi, co znaleźliśmy i co wstawić w zamian. Popraw wszystkie, zanim wgrasz ponownie, wtedy kolejne sprawdzenie przejdzie za pierwszym razem.
2. **Zleć to swojemu AI**: Naciśnij **Skopiuj polecenie dla asystenta AI** i wklej je do ChatGPT, Claude albo Gemini razem z plikami gry. Polecenie wymienia dokładne zmiany i wywołania SDK klyo.
3. **Zastąp własne logowanie**: Każdy gracz ma już konto klyo. To, co gra zapisuje w localStorage, samo idzie za zalogowanym graczem na każde urządzenie, więc usuń logowanie i formularz hasła. Wyniki z nazwą gracza daje klyo.score.
4. **Zastąp PeerJS i cudze serwery**: PeerJS pokazuje graczom nawzajem ich adresy IP i idzie przez publiczny serwer, więc na klyo nie działa. Do gry ze znajomymi użyj pokoi klyo.online. Firebase, Supabase albo PlayFab zamień na klyo.save, klyo.score i klyo.leaderboard.
5. **Usuń płatności i cudze reklamy**: Reklamy przy grze stawiamy my, a gdy ruszą na klyo, 70% przychodu jest Twoje. Nagrodę za obejrzenie reklamy daje klyo.rewardedAd, przerwę między poziomami klyo.adBreak.
6. **Połącz swoje AI z klyo**: Naciśnij **Połącz swoje AI z klyo albo weź klucz API**. Połączone AI samo wgra poprawioną wersję i sprawdza ją, aż na karcie nic nie zostanie.

## Jeśli coś nie działa

### W paczce nie ma index.html

Spakuj folder, w którym leży index.html (często dist, build albo public), z index.html na wierzchu.

### W paczce jest kilka plików index.html

Jeden ZIP to jedna gra. Zostaw jeden index.html na wierzchu.

### Plik nie należy do gry przeglądarkowej

Przyjmujemy strony, skrypty, style, obrazy, dźwięki, wideo, czcionki i dane gry. Inne pliki usuń z paczki.

### Gra z Unity nie startuje

Skompresowany build Unity czeka na nagłówek z serwera. W Player Settings, Publishing Settings ustaw Compression Format na Disabled albo włącz Decompression Fallback i zbuduj ponownie.

### Gra z Godota prosi o plik, którego nie ma w eksporcie

Karta podaje plik i sceny, które go wczytują. Przywróć plik albo wskaż w tych scenach ten, którego używasz teraz, i wyeksportuj grę ponownie. Pliki przenoś i zmieniaj im nazwy tylko w panelu FileSystem w Godocie.

### Gra z Godota długo wczytuje się na telefonie

Jej tekstury są tylko w formacie dla komputerów. W eksporcie Web zaznacz For Desktop i For Mobile w VRAM Texture Compression i wyeksportuj grę ponownie.

### Plik z CDN dalej jest na karcie

Gra składa ten adres w trakcie działania, więc nie mogliśmy go zobaczyć. Wpisz adres w kodzie jako pełny napis albo włóż plik do paczki z adresem względnym.

### Gra łączy się z moim serwerem meczów

Zgłoś adres serwera z polityką prywatności w ostatnim kroku kreatora. Gra trafi do sprawdzenia razem z serwerem.

## Dlaczego moja gra nie może wczytać Google Fonts na klyo?

Każdy plik z cudzego serwera zdradza tej firmie adres IP gracza i może się zmienić po naszym sprawdzeniu. Pliki z publicznych CDN dokładamy do paczki sami, więc gra wczytuje je z klyo i działa też bez sieci.

## Czy mogę zostawić własne logowanie i konta?

Nie. Gracze mają już konto klyo, a ich postęp z localStorage idzie za nimi na każde urządzenie bez linijki kodu. Pełny stan gry zapisze klyo.save, jeśli chcesz więcej.

## Czy mój asystent AI zna te zasady?

Tak. Łącznik klyo daje każdemu AI tę samą listę w klyo_game_requirements, a klyo_game_diagnostics mówi mu, co zatrzymało paczkę i jak to naprawić.

## Powiązane instrukcje

- [Jak wydać grę HTML5 na klyo games](https://games.klyo.pl/pl/wsparcie/jak-wydac-gre-html5/)
- [Gra pokazuje białe okno: jak to naprawić](https://games.klyo.pl/pl/wsparcie/biale-okno/)
- [Jak zapisać postęp gracza w grze HTML5](https://games.klyo.pl/pl/wsparcie/zapis-postepu/)
- [Wszystkie instrukcje](https://games.klyo.pl/pl/wsparcie/)

Nadal coś nie działa? Napisz na [kontakt@klyo.pl](mailto:kontakt@klyo.pl) i podaj adres gry. Odpowiada człowiek, w dwa dni robocze.

---

Źródło: https://games.klyo.pl/pl/wsparcie/gra-zatrzymana-przy-wgraniu/ · Autor: klyo, polska firma technologiczna (Łódź, klienci w całej Polsce) · Kontakt: kontakt@klyo.pl · Indeks dla modeli językowych: https://games.klyo.pl/llms.txt
