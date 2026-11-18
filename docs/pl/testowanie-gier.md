> **Strona kanoniczna:** https://games.klyo.pl/pl/testowanie-gier/ · aktualizacja 2026-11-18 · Plik powstaje automatycznie ze strony klyo games, więc poprawki wprowadzamy na stronie.

# Testowanie gier *z nagraniem* gry testera

Wysyłasz link do swojej gry tam, gdzie o niej mówisz. Kto zgodzi się na test, zostawia ci nagranie z obrazem gry, kursorem, stuknięciami i klawiszami. W studiu widzisz, gdzie się zgubił i w co stukał na próżno.

[Wejdź do studia twórcy](https://dev.klyo.pl/pl/)

[Asystent AI i MCP](https://games.klyo.pl/pl/mcp/)

Animacja obok to prawdziwy test FRONTBREAK z 18 listopada 2026, nagrany na zwykłym komputerze z linku twórcy.

dev.klyo.pl · Wyniki · Filmiki testerów

![Odtwarzacz nagrania testu w studiu klyo: film z gry FRONTBREAK, kursor testera i oś ze stuknięciami](https://games.klyo.pl/foto/testy-gier-film-pl-1280.408de240.jpg)

*Odtwarzacz w studiu: film z gry 3D (WebGPU), kursor testera i oś z jego stuknięciami. Długie chwile bez ruchu przeskakują same.*

## Trzy kroki do pierwszego nagrania

Link robisz w minutę, a nagranie widzisz, zanim tester skończy grać.

1. **Nazwij link**: W studiu, w Wynikach gry, tworzysz link i nadajesz mu nazwę, na przykład „Reddit”, oraz wybierasz język strony. Wejścia, osoby i testy liczą się dla każdego linku osobno, bez twoich własnych wizyt.
2. **Tester decyduje**: Zanim gra ruszy, tester widzi kartę z tym, co zapisujemy, a czego nie. Przycisk „Graj bez zapisu” uruchamia zwykłą grę. Testy są dla osób od 16 lat.
3. **Oglądasz od razu**: Nagranie pojawia się w studiu bez odświeżania strony, z kadrem gry jako okładką, datą i godziną. Gdy ktoś gra właśnie teraz, przy nagraniu świeci się znak „na żywo”.

## Film z gry, także z WebGL i WebGPU

Większość gier w przeglądarce rysuje na płótnie (canvas). Narzędzia do nagrywania stron odtwarzają kod strony, a nie jej obraz, więc płótno zostaje u nich puste. Microsoft Clarity pisze o tym wprost w swoich pytaniach i odpowiedziach.

U nas zapis gry robi zdjęcie płótna zaraz po tym, jak gra narysuje klatkę, także wtedy, gdy silnik (Three.js, Unity, Godot i inne) rysuje poza zwykłą pętlą animacji. Koder wideo przeglądarki zmniejsza obraz do 640 pikseli i 10 klatek na sekundę. Okienka i przyciski, które gra stawia w HTML nad płótnem, dokładamy osobno, więc w nagraniu widać też menu i napisy.

Każda klatka filmu ma czas gry. Kursor, palce i klawisze zgadzają się z obrazem co do klatki, a oś przewijasz jak w zwykłym filmie.

- **640 px i 10 klatek na sekundę**: Tyle wystarcza, żeby zobaczyć ruch i przeczytać napisy. Minuta gry waży około 2 MB.
- **Gra nie zwalnia**: W naszej próbie gra z filmem zrobiła 1086 klatek, a bez filmu 1107 w tym samym czasie.
- **Gry 2D i 3D**: Płótno 2D, WebGL i WebGPU. Gra bez płótna odgrywa się z zapisanych ruchów, bez filmu.
- **48 godzin**: Potem film i zapis znikają same. Wszystkie filmy razem mają twardy limit miejsca na naszym serwerze.

[Źródło: Microsoft Clarity, pytania i odpowiedzi („Clarity can't render inside third-party iFrame or canvas elements”), stan z 18 listopada 2026.](https://learn.microsoft.com/en-us/clarity/faq)

## Gdzie gra nie odpowiada

Trzy sygnały znane z analityki stron przenieśliśmy na płótno gry.

![Zbliżenie odtwarzacza: dwa martwe stuknięcia w minimapę gry FRONTBREAK z dopiskiem „nic się nie stało”](https://games.klyo.pl/foto/testy-gier-martwe-pl-720.ebfd24f0.jpg)

*Tester dwa razy stuka w minimapę FRONTBREAK i nic się nie dzieje. Odtwarzacz zaznacza oba stuknięcia jako martwe.*

- **Martwe stuknięcie**: Stuknięcie, po którym przez sekundę nic się nie zmieniło ani na obrazie gry, ani w stronie. Porównujemy z sekundą przed stuknięciem, więc animowane tło nie robi fałszywego alarmu.
- **Szał klikania**: Co najmniej trzy szybkie stuknięcia w jedno miejsce, z czego dwa martwe. Zwykle znaczy, że przycisk jest za mały, zasłonięty albo gra czeka bez żadnego znaku.
- **Pomijanie ciszy**: Gdy tester nic nie robi, a obraz stoi, odtwarzacz przeskakuje dalej i mówi, ile pominął. Gdy obraz się rusza, ta część leci cztery razy szybciej.

## Lista poprawek dla asystenta AI

Z nagrań składamy raport. Martwe stuknięcia mają nazwę elementu pod palcem i miejsce na ekranie w procentach, błędy JavaScript mają dokładną treść, a przy wyjściu z gry zapisujemy napisy, które tester miał wtedy przed oczami.

Asystent podpięty przez MCP (Claude, ChatGPT, Cursor i inne) czyta ten raport w narzędziu klyo_game_analytics jako pierwsze zadania. Ma dowód z nagrania, więc poprawia grę narzędziami klyo_game_files i klyo_game_patch, a ty sprawdzasz poprawkę nowym testem z tego samego linku.

Tak wyglądał raport po teście FRONTBREAK, w którym tester stukał w minimapę:

`Gra frontbreak: co poprawić według 5 nagrań prawdziwych testerów z ostatnich 48 h.
• Martwe stuknięcia na płótnie gry, 11% od lewej i 19% od góry ekranu: 2 w 1 z 5 nagrań
Dlaczego: Gracze stukają tu i przez sekundę nic się nie zmienia: spodziewają się przycisku, wyboru albo przejścia dalej.
Co zrobić: Obejrzyj chwilę z dowodu i sprawdź, czego gracz tu szuka.
Dowód (studio → Wyniki → Filmiki): Tester 6, 0:59`

## Co widzi twórca, a czego nie

Test jest dla gry, nie dla danych o człowieku. Te zasady obowiązują w każdym nagraniu.

- **Najpierw zgoda**: Nic nie zapisujemy przed kliknięciem „Graj i pomagaj”. Zgodę tester cofa przyciskiem „Test · Zatrzymaj” na grze.
- **Pseudonim zamiast nicku**: Twórca widzi „Tester 6”, kraj i rodzaj urządzenia. Konta testera ani jego nicku nie widzi.
- **Tylko gra**: Nagrywamy samą grę. Reszta ekranu, kamera, mikrofon i tekst wpisany w pola zostają poza nagraniem.
- **Znika po 48 godzinach**: Tester usuwa swój zapis od razu po teście, a twórca usuwa nagranie jednym przyciskiem w studiu.
- **Na naszym serwerze**: Nagrania leżą na serwerze klyo, nie w chmurze innej firmy. Jeden test to najwyżej 48 MB.
- **Od 16 lat**: Kliknięcie „Graj i pomagaj” jest potwierdzeniem, że tester ma co najmniej 16 lat.

Pełne zasady są w [polityce prywatności](https://games.klyo.pl/pl/polityka-prywatnosci/), w części o testach gier.

## Zrób pierwszy test jeszcze dziś

Załóż konto twórcy, wgraj grę i utwórz link testowy w Wynikach. Pierwsze nagranie zobaczysz kilka minut po tym, jak ktoś zagra.

[Wejdź do studia twórcy](https://dev.klyo.pl/pl/)

[Asystent AI i MCP](https://games.klyo.pl/pl/mcp/)

---

Źródło: https://games.klyo.pl/pl/testowanie-gier/ · Autor: klyo, polska firma technologiczna (Łódź, klienci w całej Polsce) · Kontakt: kontakt@klyo.pl · Indeks dla modeli językowych: https://games.klyo.pl/llms.txt
