> **Strona kanoniczna:** https://games.klyo.pl/pl/mcp/ · aktualizacja 2026-09-24 · Plik powstaje automatycznie ze strony klyo games, więc poprawki wprowadzamy na stronie.

# Serwer MCP klyo: wydaj grę HTML5 asystentem AI

MCP (Model Context Protocol) to otwarty standard, przez który asystenci AI sięgają po cudze narzędzia. U nas służy do wydawania gier. Robisz grę razem z Claude albo ChatGPT? Może ją u nas wydać sam: wysyła paczkę, wypełnia opis, a ty dostajesz gotową grę do obejrzenia i jeden przycisk. Bez przeklikiwania formularza po każdej poprawce.

[**klyo**dev
**Wróć do studia twórcy**Tam wydajesz klucz, wgrywasz paczkę i wypuszczasz gotową grę.](https://dev.klyo.pl/pl/)

## Jak to podłączyć

1. **Podpisz zasady w przeglądarce**: Wejdź na [dev.klyo.pl](https://dev.klyo.pl/) i przyjmij regulamin dla twórców. Tego kroku asystent nie zrobi za ciebie i tak ma być: umowę podpisuje człowiek.
2. **Dodaj klyo do swojego asystenta**: Najprościej: [**podłącz jednym kliknięciem**](https://panel.klyo.pl/mcp/connect): wybierasz swoje AI (Claude, ChatGPT, Gemini, Copilot, Claude Code, opencode), resztę robimy za Ciebie. Ręcznie: w ustawieniach asystenta dodaj serwer narzędzi (MCP) pod adresem `https://panel.klyo.pl/mcp?profil=gry`. Zalogujesz się swoim kontem klyo i zdecydujesz, na co się zgadzasz, tak samo jak przy podłączaniu dysku albo poczty.
3. **Powiedz, co ma zrobić**: „Wydaj tę grę na klyo, paczka leży pod tym adresem” wystarczy. Asystent poda adres paczki ZIP, nazwę, opis dla gracza i odpowiedzi ankiety wieku. Chcesz tablicę wyników i miejsce na hubie rekordów? Powiedz „dodaj tablicę wyników klyo”, a narzędzie klyo_game_sdk opisze mu wywołania (gotowa → postęp → wynik) i próg wyniku.
4. **Obejrzyj i wypuść**: Gra czeka w studiu z podglądem i kodem QR. Zagrywasz w nią na telefonie, a potem klikasz „Wypuść do katalogu”. Dopiero to kliknięcie stawia grę przed graczami.

## Twoje AI w studiu, na twoim planie

Działa to tak samo jak w VS Code i Cursorze: asystent AI pracuje po twojej stronie, w ramach twojej subskrypcji Claude lub ChatGPT, a dane logowania pozostają na twoim urządzeniu. klyo nie uruchamia asystenta na swoich serwerach i nie ma dostępu do twojego logowania. Otrzymujemy wyłącznie gotowy tekst, który publikujemy dopiero po twojej akceptacji.

1. **„Wypełnij swoim AI” w formularzu nowej gry**: Jeden przycisk na cały formularz. Twoje AI wpisuje nazwę, hasło, opis po angielsku i po polsku, rodzaj, sterowanie i czas partii, a ty patrzysz, jak pola wypełniają się na żywo. Jedno pole poprawiasz w tej samej rozmowie, na przykład „skróć hasło”, i formularz zmienia się od razu. Ankietę treści zaznaczasz sam.
2. **„Przetłumacz swoim AI” w oknie tłumaczeń**: Języki wybierasz przyciskami w oknie, brakujące są już zaznaczone. Kolejne możesz dopisać później w rozmowie, na przykład „a teraz niemiecki”. Każde tłumaczenie trafia do okna „Tłumaczenia” jako propozycja: sprawdzasz je i klikasz „Zatwierdź”. Google liczy dopiero tekst zatwierdzony przez człowieka.
3. **„Napisz swoim AI” przy wizytówce**: Twoje AI pisze „o mnie” i hasło pod twoją nazwą wyłącznie na podstawie twoich gier. Pokazuje ci tekst i zapisuje go dopiero po twojej zgodzie.
4. **Okno sprawdza połączenie**: Po kliknięciu okno mówi, czy twoje AI jest połączone z klyo, na podstawie tej samej listy co strona połączeń. Połączone: znak ✓ i przycisk „Otwórz w Claude” albo „Otwórz w ChatGPT”. Niepołączone: najpierw „Połącz klyo ze swoim AI”. Robisz to raz.

Pracujesz w Claude Code, Cursorze albo VS Code? W oknie kliknij „Skopiuj polecenie” i wklej je tam. Narzędzia są te same.

## Czego asystent NIE może

**Podpisać za ciebie umowy.** Regulamin dla twórców przyjmujesz w przeglądarce, na swoim koncie. Bez tego narzędzie odmawia z jasnym powodem, a nie po cichu.

**Wypuścić gry do katalogu.** Asystent doprowadza grę do stanu „czeka na ciebie”. Ostatni krok (ten, po którym gra jest widoczna dla ludzi) należy do człowieka.

**Zaznaczyć za ciebie ankiety treści ani oświadczeń.** Z ankiety wynika wiek i reklamy przy grze, więc to deklaracja człowieka. Asystent wypełnia resztę formularza, ankietę klikasz ty.

**Dotknąć twoich pieniędzy.** Numer konta, dane do rozliczeń i wypłaty są poza zasięgiem narzędzi. Asystent nie zobaczy ich i nie zmieni.

**Ominąć sprawdzenia.** Paczka przechodzi to samo sito co przy wgraniu z przeglądarki: rozmiar, liczba plików, cudze reklamy, złośliwy kod, wulgaryzmy w nazwie i opisie, ankieta wieku.

## Jesteśmy w oficjalnym rejestrze MCP

Rejestr Model Context Protocol to spis, z którego asystenci i programiści biorą serwery narzędzi. Żeby do niego wejść, trzeba udowodnić, że domena naprawdę należy do nas. Potwierdziliśmy to podpisem klucza w DNS klyo.pl. To nie jest katalog, do którego się wpisuje. To katalog, do którego się wchodzi.

- **Nie musisz nam wierzyć na słowo.** Wpis jest publiczny i każdy może go sprawdzić, razem z adresem naszego serwera i stroną, którą właśnie czytasz.
- **Twój klient sam nas znajdzie.** Narzędzia czytające rejestr podpowiedzą klyo, gdy zapytasz o wydanie gry. Bez szukania adresu po forach.
- **Nazwa jest nasza na stałe.** `pl.klyo` to nasza przestrzeń w rejestrze; nikt inny się pod nią nie wystawi, bo nie ma dostępu do naszej domeny.

## Inne serwery MCP do wydawania gier przeglądarkowych

Nie jesteśmy jedynym serwerem MCP, który wydaje gry przeglądarkowe. Oto, co każdy z nich daje grze i twórcy, żebyś mógł wybrać sam.

| | klyo games | Playgama | AIGameShare | Playfrog |
| --- | --- | --- | --- | --- |
| Narzędzia dla twórcy | 20 | 25+ | 5 | 2 |
| Logowanie | OAuth 2.1, nic nie wklejasz | OAuth 2.1 | token z konta wklejany do konfiguracji | brak; osobny token zarządzania dla każdej gry |
| Paczka | ZIP do 100 MB i 5 000 plików | ZIP do 300 MB | HTML do 2 MB albo ZIP do 30 MB | do 2,5 MB |
| Co dostaje gra | własny adres g-.klyo.pl, stronę w katalogu po angielsku i po polsku, tablicę wyników, klipy graczy, statystyki dzień po dniu | publiczny link do gry z piaskownicy Playgama | link do udostępnienia z zagraniami, polubieniami i tablicą wyników | link do gry; grę trzeba przejąć w ciągu 7 dni |
| Pieniądze dla twórcy | 70% przychodu z reklam od dnia akceptacji portalu przez Google AdSense (jeszcze nie) | reklamy przez Playgama po przekroczeniu progu sesji; wypłaty od 100 USD | nie podają | nie podają |

Sprawdzone 23 września 2026 w dokumentacji każdego serwisu: [Playgama](https://github.com/Playgama/developer-cabinet-mcp), [AIGameShare](https://www.aigameshare.com/developers), [Playfrog](https://glama.ai/mcp/connectors/games.playfrog/publish). Zasady tamtych serwisów zmieniają się bez zapowiedzi; jeśli coś się rozjechało, napisz, a poprawimy tego samego dnia.

## Co jeszcze potrafią narzędzia

| `klyo_my_games` | wypisuje twoje gry i ich stan: czeka, w katalogu, wstrzymana, odrzucona z powodem |
| --- | --- |
| `klyo_publish_game` | wysyła paczkę i przygotowuje grę do wypuszczenia: nazwa, hasło, opis po angielsku i po polsku, rodzaj, ankieta treści; te same pola i limity co w kreatorze |
| `klyo_game_stats` | wejścia i zagrania dzień po dniu |
| `klyo_game_requirements` | kontrakt produkcyjny gry, pierwsze wywołanie agenta: ekrany, wejście, cykl gry, dźwięk, grafika, warstwa społeczna, test lokalny, bramka jakości, etapy wydania |
| `klyo_game_scaffold` | Klyo Kit, szkielet gry na poziomie studia: pliki-startery i API (menu, pauza, koniec, dźwięk, motyw, wejście, online, hot-seat); asystent pisze tylko rozgrywkę |
| `klyo_release_rollback` | cofnięcie gry do poprzedniej wersji jednym ruchem: pliki poprzedniej leżą obok, nic nie trzeba wgrywać |
| `klyo_game_diagnostics` | dlaczego gra nie wstała: brakujące pliki i błędy z przeglądarki, po kolei, a do tego dopasowanie do ekranów, bramka jakości (krytyczne / ostrzeżenia), a z `zmierz: true` pomiar na żądanie dla asystenta bez przeglądarki |
| `klyo_game_files` | czyta pliki twojej gry albo paczki z poczekalni: spis ze skrótami, treść pliku, różnice nowej wersji względem tej, w którą grają gracze |
| `klyo_game_patch` | poprawia pliki gry bez ZIP-a, w warsztacie obok wersji u graczy; z `nowa` zaczyna grę od zera ze szkieletu Klyo Kit, z `from_upload` dokłada obraz, dźwięk albo czcionkę; wypuszczasz jak każdą nową wersję |
| `klyo_delete_game` | zdejmuje twoją grę z portalu: adres zostaje twój i możesz wgrać grę z powrotem; drugie wywołanie usuwa ją z twojej listy na dobre, a wyniki zostają przy adresie |
| `klyo_fix_game` | poprawia TREŚĆ wydanej gry (opis, jak grać, ile trwa partia, rodzaj, nastrój) bez ruszania paczki, więc bez ponownego badania plików |
| `klyo_game_cover` | kafel, po którym gracz pozna grę: klatki są zdjęciami z twojej działającej gry, więc okładka pokazuje to, co gracz naprawdę zobaczy |
| `klyo_game_sdk` | co gra może zawołać u nas: tablica wyników, zapis postępu, pełny ekran, reklama za nagrodę, klip. Przeczytaj to, ZANIM napiszesz grę |
| `klyo_update_game` | wgrywa nową wersję gry, która już stoi w katalogu: paczka trafia do poczekalni z adresem podglądu, a odpowiedź niesie pomiar z plików: ile % kodu, wyglądu i dźwięku się zmieniło, nowe pliki i napisy, rodzaj zmiany |
| `klyo_release_version` | wypuszcza czekającą wersję do graczy, ten sam krok co „Wypuść” w studiu; rodzaj zmiany domyślnie z pomiaru, „co nowego” przy nowej funkcji |
| `klyo_upload_package` | wysyła paczkę prosto z twojego dysku, bez publicznego adresu |
| `klyo_fill_game_form` | wypełnia na żywo otwarty formularz „Nowa gra” w studiu; ty patrzysz i poprawiasz, ankiety i oświadczeń nie dotyka, publikujesz sam |
| `klyo_game_translate` | tłumaczenia tekstów gry robione przez twoje AI: najpierw oryginał i brakujące języki, potem propozycje, które zatwierdzasz w studiu |
| `klyo_creator_card` | wizytówka twórcy: „o mnie” i hasło pisane na podstawie twoich gier, zapis dopiero po twojej zgodzie |
| `klyo_add_post` | wpis w społeczności: pytanie, prośba o testy, premiera |

## Pola i reguły: te same co w kreatorze

Asystent wypełnia dokładnie to, co człowiek klika w studiu. Limity stoją w schemacie narzędzia (bramka przed wywołaniem), a serwer sprawdza je drugi raz i odpowiada kodem błędu wskazującym pole.

| Nazwa | Do 30 znaków, jak w Google Play i App Store: sama nazwa gry, bez hasła i bez „zagraj za darmo”. Nie od cudzej marki. |
| --- | --- |
| Hasło pod nazwą | **Obowiązkowe.** Jedno zdanie do 80 znaków, bez kropki: czym gra jest, słowami, których gracz szuka. Stoi jako H2 i w tytule karty w Google. |
| Opis | **Minimum 25 słów**, do Google około 220 (krótszy = strona gry poza wyszukiwarką). Co się robi, jak wygląda partia, dla kogo, czym się różni. Jak człowiek: bez pauz „—”, bez „zanurz się”, bez list. |
| Język tekstu | Pole `jezyk_tekstu` (pl, en, de, fr, es, pt, it, ru, uk, tr) mówi, w jakim języku napisano teksty. **Pozostałe języki tłumaczy twoje AI** narzędziem `klyo_game_translate`, na twoim planie; każdy język przechodzi sprawdzenie i czeka w studiu na twoje „Zatwierdź”. Znaczniki `…` tylko dla wersji, którą twórca naprawdę napisał sam. |
| Rodzaj, półki, nastrój | Rodzaj z listy, do trzech; półki katalogu i nastrój opcjonalnie; listy są w schemacie i pochodzą z tego samego pliku, którym filtruje katalog. |
| Ankieta treści | **Dziesięć pytań tak/nie** (obiekt `ankieta`): przemoc rysunkowa, realistyczna, strach, wulgaryzmy, nagość, używki, hazard, interakcje, zakupy, dostęp do lokalizacji. Z odpowiedzi wynika etykieta wieku, reklamy i wejście do aplikacji w sklepach. Asystent ma zapytać twórcę, nie zgadywać. |
| Wiek od twórcy | `wiek_min` (3, 7, 12, 16, 18) może tylko podnieść etykietę ponad wynik ankiety, nigdy jej nie obniża. |
| Etap gry | `etap`: `w_budowie`, `demo` albo `gotowa`; przy dwóch pierwszych `etap_dni` (7 lub 30) mówi, kiedy przypomnieć o decyzji. **Asystent ma o to zapytać.** |
| Sklepy | `sklep_play` i `sklep_apple`: adresy tej samej gry w Google Play i App Store: odznaki na stronie gry i w tekstach udostępnienia. |
| Jak grać, partia, układ, wynik | Sterowanie na telefonie i komputerze (do 300 znaków), czas partii (do 40), układ poziom/pion/oba, najwyższy możliwy wynik jako zapora na tablicy. |

## Własny agent: klucz zamiast logowania

Claude i ChatGPT logują się na twoje konto same. Jeśli piszesz własnego agenta albo skrypt, dostaniesz klucz i podasz go w nagłówku. To ta sama droga i te same narzędzia, tylko bez okna logowania.

1. **Wygeneruj klucz w studiu**: Na [dev.klyo.pl](https://dev.klyo.pl/), w polu „Integracja z serwerem (API)”, kliknij „Wygeneruj klucz”. Pokazujemy go raz, więc zapisz go od razu. Klucz zaczyna się od `klyo_sk_` i możesz go w każdej chwili unieważnić.
2. **Podaj go przy połączeniu**: Nagłówek `Authorization: Bearer klyo_sk_…` przy adresie `https://panel.klyo.pl/mcp?profil=gry`. Twój agent widzi dokładnie te narzędzia co Claude, ani jednego więcej.
3. **Sprawdzaj, co robi gra**: Po otwarciu podglądu wywołaj diagnozę. Dostaniesz pliki, o które gra prosiła, a których nie ma w paczce, i błędy z przeglądarki, zamiast zgadywania z białego okna.

### Przykład: pytanie o diagnozę

`curl -s "https://panel.klyo.pl/mcp?profil=gry" \
-H "Authorization: Bearer klyo_sk_TWOJ_KLUCZ" \
-H "Content-Type: application/json" \
-d '{"jsonrpc":"2.0","id":1,"method":"tools/call",
"params":{"name":"klyo_game_diagnostics",
"arguments":{"slug":"lumina-thief"}}}'`

## Twoja przeglądarka jest okiem

Nie mamy farmy przeglądarek i nie potrzebujemy jej. Gra uruchamia się u ciebie, na twoim procesorze, a nasz czujnik w stronie podglądu melduje nam, co się w niej wysypało. Dzięki temu asystent widzi to samo, co zobaczyłbyś ty, otwierając grę.

1. **Otwórz podgląd u siebie**: Playwright, zwykły Chrome albo telefon z kodu QR. Dopisz do adresu `?s=twoj-znacznik` (dowolne 1–24 znaki).
2. **Pograj naprawdę**: Kliknij, przesuń, poczekaj na drugą planszę. Czujnik zbiera wyjątki, nieudane pliki, wpisy z konsoli i to, czy gra w ogóle wystartowała.
3. **Zapytaj o diagnozę**: `klyo_game_diagnostics` z polem `sesja` równym twojemu znacznikowi. Dostaniesz WYŁĄCZNIE błędy ze swojego przebiegu, a do tego liczbę cudzych, żeby nic nie znikło po cichu.

Kolejność ma znaczenie: pytanie zadane przed otwarciem gry zwróci pustą odpowiedź, bo nie było czego zebrać.

## Paczka z dysku, bez wystawiania gry światu

Nie stawiaj tunelu i nie wrzucaj niewydanej gry na publiczny hosting. Narzędzie `klyo_upload_package` oddaje asystentowi **bilet wgrywania** (token ważny godzinę, który otwiera wyłącznie wysyłanie plików na twoje konto) oraz listę paczek, które już czekają u nas bez gry. Asystent z powłoką (Claude Code, Codex, Cursor) wysyła plik sam, w dwóch żądaniach; asystent w rozmowie (claude.ai, ChatGPT) prosi cię, żebyś wgrał ZIP w studiu: paczka ląduje w poczekalni, nic się nie publikuje, a on bierze jej numer z listy. Poniżej ten sam przepis w skrócie.

1. **Zapowiedz plik**: `POST /api/upload/init` z nagłówkiem `Authorization: Bearer ` i `{ filename, total_size, content_type }` → dostajesz `upload_id` i `chunk_size`.
2. **Wyślij bajty**: `PATCH /api/upload/` z tym samym biletem, `Upload-Offset` i `Content-Type: application/offset+octet-stream`. Do 32 MB jednym żądaniem; większy plik w kawałkach. Przerwane wysyłanie wznów: `HEAD` poda, ile już mamy.
3. **Wydaj albo podmień**: `klyo_publish_game` lub `klyo_update_game` z `upload_id` zamiast `zip_url`.

Publiczny adres ZIP-a zostaw dla gry, która naprawdę stoi już w sieci, na przykład przy przenoszeniu z itch.io.

## Standard produkcyjny gry: asystent zna minimum, zanim napisze kod

Zwykły człowiek pisze do swojego asystenta „chcę grę w statki”. Asystent podłączony do klyo najpierw woła `klyo_game_requirements` i dostaje kontrakt: telefon, tablet i komputer; dotyk, mysz i klawiatura; pion i poziom z reakcją na zmianę rozmiaru; dźwięk z odzyskaniem po powrocie z tła; zapis, tablica wyników, pauza i powtórka jednym gestem; jedna paleta i jeden styl; bez cudzych marek i bez cudzych reklam. Nie pyta o to użytkownika, tylko od razu buduje na tym poziomie. Wersja 1 standardu jest zamrożona od 23.09.2026: nowy wymóg dochodzi tylko wtedy, gdy prawdziwa gra na klyo trafi na prawdziwy problem.

1. **Test u siebie, nie na naszym serwerze.** Asystent pobiera `games.klyo.pl/sdk/klyo-test.mjs` i uruchamia go lokalnie: cztery ekrany, przewijanie, ułamek ekranu, tekst, nasłuchy dotyku, waga, czas, wyjątki. Przed wydaniem dokłada `--slaby-telefon --jezyki`: tani telefon i oba języki. Wynik ma `krytyczne` i `ostrzezenia`, więc poprawia i testuje w pętli, aż przejdzie. Ciężką pracę robi komputer twórcy; klyo mierzy przy wgraniu i wydaniu tym samym plikiem.
2. **Bramka jakości, także dla paczki wgranej ręcznie.** Każda paczka w poczekalni jest mierzona na czterech ekranach zaraz po wgraniu; `klyo_game_diagnostics` i okno podglądu w studiu pokazują tę samą `bramka`: wyjątki, brakujące pliki, cudze reklamy, brak zestawu, brak dotyku i przewijanie blokują wydanie jako „gotowa” (demo i „w budowie” przechodzą); mały ekran, mały tekst, waga, brak tablicy i cudze marki wymagają powodu.
3. **Etapy wydania.** Lokalnie → podgląd (`g-podglad-…`, poza katalogiem i Google) → publikacja z etapem `w_budowie` / `demo` / `gotowa` → nowa wersja z podglądem, gracze grają w starą, poprzednia zostaje do przywrócenia. Człowiek zatwierdza dwa momenty: publikację i wypuszczenie wersji.

## Nowa wersja gry: przez asystenta tak samo jak w studiu

Trzy kroki, te same co przyciski „Nowa wersja” i „Wypuść” w studiu. Asystent nie zgaduje, co się zmieniło: mierzymy to z plików i mówimy mu, co z tego wynika dla klipu. **Klip do nowej wersji nagrywasz sam**: w studiu, po wypuszczeniu (okno nagrywania otwiera się samo przy nowym wyglądzie albo funkcji).

1. **Wgraj**: `klyo_update_game` z `slug` i `upload_id` (plik z dysku) albo `zip_url`. Gra w katalogu nie zmienia się od razu: nowa wersja czeka w poczekalni pod własnym adresem podglądu. Odpowiedź: `zmiana` (kod / wygląd / dźwięk w %, nowe pliki i napisy, `podpowiedz`: poprawka | funkcja | interfejs), `adres_nowej`, `wyrok` i `dalej`.
2. **Zagraj**: To twoje sprawdzenie, nie asystenta: otwórz adres podglądu, najlepiej na telefonie. Studio pokazuje tę samą wersję w oknie gry z torem „wersja → zagraj → wypuść → klip”.
3. **Wypuść**: `klyo_release_version` z `slug`; `zmiana` pomiń (weźmiemy zmierzoną) albo podaj, gdy wiesz lepiej; `nowosc` to jedno zdanie do feedu przy nowej funkcji. Przed podmianą cała nowa wersja przechodzi sito jeszcze raz. Gracze dostają ją od razu (kto gra, wybiera: zaktualizuj albo dokończ partię), poprzednia zostaje u nas, strona gry się przebudowuje, a ekrany mierzymy raz, po wypuszczeniu. Obserwujący dostają powiadomienie, gdy gra jest w katalogu.

Skutek dla klipu: przy poprawce klip zostaje; przy nowej funkcji klip zostaje, a „co nowego” idzie do feedu jako „Nowość”; przy nowym wyglądzie (interfejs) stary klip schodzi z kafelka i z feedu, dopóki nie nagrasz nowego w studiu.

## Poprawka bez ZIP-a: warsztat gry

Asystent czyta pliki twojej gry i poprawia je u nas, bez paczki od ciebie. Działa to z grą w katalogu i z paczką, która czeka w poczekalni. Gracze do końca grają w wersję, którą znają: poprawki trafiają do warsztatu, czyli nowej wersji obok, z własnym adresem podglądu. Wypuszczasz ją tak samo jak każdą nową wersję.

1. **Zacznij od zera, jeśli gry jeszcze nie ma**: `klyo_game_patch` z `nowa` (`plansza`, `zrecznosciowa` albo `logiczna`) zakłada paczkę ze szkieletu Klyo Kit prosto w poczekalni i w tym samym wywołaniu wpisuje rozgrywkę. Asystent w rozmowie, bez dysku i bez ZIP-a, ma od tej chwili własną grę pod adresem podglądu.
2. **Przeczytaj**: `klyo_game_files` z `slug` gry albo `upload_id` paczki. Bez `path` dostajesz spis plików ze skrótem `hash`, z `path` treść pliku (do 200 KB naraz, dalej od `from_line`), a z `changes: true` różnice nowej wersji względem tej u graczy.
3. **Popraw**: `klyo_game_patch` z listą `edits`: dokładny fragment `old_string` zamieniony na `new_string`, cały plik w `content` albo `delete: true`. Przy pliku, który istnieje, podajesz `expected_hash` z odczytu: jeśli ktoś zmienił plik w międzyczasie, nic się nie zapisze. Zmiany z jednego wywołania wchodzą wszystkie albo żadna. Pierwsza poprawka otwiera warsztat, a studio od razu pokazuje go jako „Nowa wersja czeka”.
4. **Zagraj i sprawdź**: Adres podglądu przychodzi w odpowiedzi. Otwórz go (najlepiej na telefonie), a `klyo_game_diagnostics` pokaże błędy, brakujące pliki i sito właśnie tej wersji, a nie tej u graczy. Asystent bez przeglądarki podaje `zmierz: true`: otwieramy podgląd za niego i oddajemy błędy oraz miniatury czterech ekranów pod pełnymi adresami, więc widzi, jak gra wygląda. Pliki bez zmian od pomiaru nie uruchamiają przeglądarki drugi raz; jeden pomiar naraz na konto, sześć na godzinę.
5. **Wypuść**: Gra: `klyo_release_version` albo „Wypuść” w studiu. Paczka z poczekalni: `klyo_publish_game` wyda ją razem z poprawkami. Przed podmianą cała gra przechodzi sito jeszcze raz.

- **Wersja u graczy się nie zmienia.** Warsztat to kopia obok, a każdy zapis tworzy nowy plik, więc to, co pobierają gracze, nie zmienia się ani na chwilę.
- **Tekst w rozmowie, pliki biletem.** Treść zmiany zapisuje pliki tekstowe (html, htm, js, mjs, css, json, svg, txt, xml, webmanifest). Obraz, dźwięk, czcionkę albo duży plik (do 20 MB) asystent wysyła biletem z `klyo_upload_package` i podaje w `from_upload`: bez base64, a początek pliku musi pasować do rozszerzenia.
- **To samo sito co przy wgraniu.** Każdy zmieniony plik sprawdzamy od razu: złośliwy kod, cudze reklamy, nic spoza klyo. Odmowa nie zapisuje niczego.
- **Limity.** Plik do 1 MB, jedno wywołanie do 256 KB i 20 zmian, trzy otwarte warsztaty na konto i jeden na grę, do 300 poprawek na godzinę. Wypuszczeń, cofnięć i nowych paczek do 10 na godzinę: każde uruchamia pomiar ekranów, a przeglądarka do pomiarów jest jedna dla wszystkich twórców.
- **Porządek.** Warsztat bez zmian przez 7 dni wygasa, a wersja u graczy zostaje nietknięta. Podgląd, na który nic już nie wskazuje, znika po 7 dniach. Adresy podglądów nie trafiają do Google.
- **Ślad.** Każda poprawka zapisuje się w dzienniku twojego konta: plik, skrót przed i po, rozmiar.
- **Cofanie w trakcie pracy.** Przed każdą poprawką zapisujemy punkt `auto-N` (jest w odpowiedzi), a asystent może nazwać własny przez `checkpoint`. `revert` wraca do dowolnego punktu, `discard` porzuca cały warsztat. To nie jest cofnięcie wydania: gracze nic z tego nie widzą.
- **Przed wydaniem także słaby telefon.** Przy wgraniu i wypuszczeniu mierzymy grę jeszcze raz na telefonie z procesorem spowolnionym czterokrotnie i siecią jak słabe 3G: płynność, zacięcia, pamięć i czas do pierwszej klatki. Poniżej 15 klatek na sekundę gra nie przejdzie bramki jako gotowa. Asystent bez przeglądarki zamawia ten sam pomiar przed wydaniem: `klyo_game_diagnostics` z `zmierz` i `pelny`.
- **W każdym języku gry.** Klyo Kit mówi dziesięcioma językami (polski, angielski, niemiecki, francuski, hiszpański, portugalski, włoski, rosyjski, ukraiński, turecki), a gra tymi, w których ma swoje napisy. Ten sam telefon otwieramy w każdym zadeklarowanym języku, z miniaturą. Klucz zamiast słowa i język zadeklarowany, którego gra nie pokazuje, blokują wydanie; angielski w miejscu tłumaczenia, zdanie takie samo jak po angielsku i tekst, który nie mieści się w przycisku albo wychodzi poza ekran, to ostrzeżenia. Napisy rysowane na płótnie sprawdzasz na miniaturach obok siebie.
- **Wolne klatki z przyczyną.** Sama liczba klatek nie mówi, czyja to wina. Mierzymy osobno czas kodu gry w każdej klatce, pracę przeglądarki i to, jaka część obrazu naprawdę się zmienia. Wolny kod to `niski_fps`; lekki kod i wolne rysowanie to `wolne_rysowanie` z radą, co rysować raz, a co co klatkę.
- **Bezpieczeństwo.** Kod gry otwieramy u siebie wyłącznie w odizolowanej przeglądarce, bez dostępu do naszej sieci wewnętrznej. Gra pod własnym adresem nie może też działać w imieniu zalogowanego gracza.

## Przegląd jakości premium: siedem punktów przed wydaniem

Bramka łapie błędy, ale nie powie, czy gra wygląda tanio. Dlatego asystent, zanim wyda grę jako gotową albo wypuści nowy wygląd lub funkcję, przechodzi siedem punktów i przy każdym podaje dowód: co konkretnie zrobił. Nie oceniamy gustu i nie mamy własnego modelu. Zestawiamy deklarację ze śladami w kodzie i pokazujemy ci w studiu punkty, których kod nie potwierdza, zanim klikniesz „Wypuść”.

- **Grafika:** jeden kierunek artystyczny: jedna paleta, jeden styl, scena i elementy z jednej skóry, żadnych gołych prostokątów.
- **Animacja:** każda zmiana stanu ma przejście, jest animacja wygranej i przegranej, a ruch wyłącza się u osób, które tego chcą.
- **Dźwięk:** dźwięk na każdą akcję i każdy wynik, wyciszenie w ustawieniach, powrót dźwięku po wyjściu z tła.
- **Reakcja na ruch:** odpowiedź na każdą akcję w 100 ms: obraz, dźwięk, na telefonie wibracja; widać, czyj ruch i dlaczego ruch jest niedozwolony.
- **Motyw jasny i ciemny:** oba warianty według ustawień urządzenia i przełącznik w grze.
- **Języki:** wszystkie napisy z tabeli tłumaczeń, co najmniej polski i angielski, każdy zadeklarowany język sprawdzony na telefonie (nie dotyczy gry bez słów).
- **Online:** zaproszenie linkiem, czekanie na przeciwnika, powrót po rozłączeniu, rewanż jednym gestem (nie dotyczy gry solo).

Tablica wyników: gra, która deklaruje wynik (`wynik_max`), a nie wysyła go przez `klyo.score`, nie przejdzie bramki jako gotowa. Gra bez punktów podaje powód w opisie. Przy demo i grze w budowie przegląd można pominąć, a przy samej poprawce (`zmiana: "poprawka"`) też.

## Częste pytania

### Co tu znaczy MCP?

Model Context Protocol: otwarty standard, przez który asystent AI woła narzędzia na cudzych serwerach. To nie jest hosting. Platformą jest klyo games, a MCP to sposób, w jaki twój asystent z nią rozmawia: wysyła paczkę, wypełnia opis i oddaje link do gry.

### Którzy asystenci AI wydadzą grę na klyo?

Każdy klient, który obsługuje zdalne serwery MCP z logowaniem. Instrukcje krok po kroku mamy dla: Claude (claude.ai, aplikacje i Claude Code), ChatGPT w trybie dewelopera, Cursor, VS Code z Copilotem, opencode i Gemini Enterprise. Adres serwera dodajesz raz; pierwsze wywołanie narzędzia otwiera logowanie klyo i zakłada konto.

### Skąd asystent weźmie adres paczki?

Z miejsca, w którym już pracujecie: repozytorium, dysk, własny serwer. Adres musi być publiczny i prowadzić prosto do pliku ZIP, w którym na wierzchu leży `index.html`. Paczka może ważyć do 100 MB i zawierać do 5 000 plików.

### Czy to działa z Unity i Godotem?

Tak, jeśli eksportujesz do przeglądarki. Przyjmujemy pliki WebAssembly, dane Unity i paczki Godota tak samo jak zwykły HTML z JavaScriptem.

### Co, jeśli gra nie wstanie?

Zobaczysz to w podglądzie, zanim cokolwiek wypuścisz. Jeśli grze brakuje pliku, powiemy którego, a przy przenoszeniu z innego portalu dobierzemy brakujące pliki spod adresu źródłowego.

### Czy asystent poprawi grę bez paczki ZIP?

Tak. `klyo_game_files` czyta pliki gry, a `klyo_game_patch` poprawia pliki tekstowe w warsztacie, obok wersji, w którą grają gracze. Zmiany widzisz w studiu jako „Nowa wersja czeka” i wypuszczasz je jednym kliknięciem. Obrazy i dźwięki nadal podmienia się paczką.

### Agent widzi, co się dzieje w grze?

Widzi to, co widziałaby konsola przeglądarki po twojej stronie: pliki, o które gra poprosiła bezskutecznie, i błędy JavaScriptu w kolejności, w jakiej wystąpiły. Zbieramy je, dopóki gra CZEKA: w podglądzie paczki i pod własnym adresem przed twoim kliknięciem „Wypuść do katalogu”. W chwili publikacji przestajemy: gra należy wtedy do gracza i nie wysyła nam niczego.

### Czy klyo płaci za moje AI albo widzi moje logowanie?

Nie. Twoje AI działa na twojej subskrypcji, a logowanie zostaje u ciebie, tak jak w VS Code i w Cursorze. My dostajemy tylko gotowy tekst i nic nie publikujemy bez twojej zgody.

### Jak wybrać języki tłumaczenia?

W oknie „Przetłumacz swoim AI” klikasz języki, które chcesz. Możesz też napisać w rozmowie „a teraz niemiecki”. Każdy język pojawia się w oknie „Tłumaczenia” do zatwierdzenia.

### Skąd wiem, że moje AI jest połączone z klyo?

Okno w studiu pokazuje to po kliknięciu: znak ✓ i nazwę połączonego AI. Pełna lista połączeń i odłączanie są na [stronie połączeń](https://panel.klyo.pl/mcp/connect).

### Dlaczego strony mojej gry nie ma w Google?

Strona gry wchodzi do Google, gdy w danym języku ma co najmniej 220 słów opisu napisanego albo przyjętego przez twórcę oraz nazwę i hasło w tym języku. Krótsza ma zakaz indeksowania, żeby cienka strona nie ciągnęła w dół całego portalu. Tak samo strona, która w ponad 42% powtarza inną stronę gry: wtedy dopisz zdania, które mówią tylko o tej grze. `klyo_my_games` pokazuje przy każdej grze w `tlumaczenia.indeks` powód z liczbami, na przykład „opis ma 198/220 słów”. Strony gier są po polsku i po angielsku, a teksty mogą mieć dziesięć języków.

### Jak sprawdzić, co Google widzi teraz?

`klyo_game_stats` z `sprawdz_google: true` pyta Google o strony gry w tej chwili (raz na godzinę na grę) i przy każdej stronie podaje, kiedy pytaliśmy i kiedy robot Google był na niej ostatnio. O ponowne zindeksowanie zwykłej strony prosi się w Search Console przyciskiem przy adresie: Google nie przyjmuje takiej prośby przez API, a mapa witryny zgłasza stronę sama.

### Kiedy powstaje strona kategorii, na przykład pasjans?

Gdy w kategorii są co najmniej trzy gry. Strona z jedną grą to dla Google kopia kafla, a za takie strony obniża cały portal. Pierwsza gra w kategorii może zajść wysoko sama, stroną gry z pełnym opisem; strona kategorii dołączy przy trzeciej.

### Mój klucz nie widzi części narzędzi. Co zrobić?

`klyo_status` wypisuje ukryte narzędzia, powód (zakres albo rodzaj konta) i sposób odblokowania. Zakres `klyo:publish` obejmuje poprawki podglądu (`klyo:edit_preview`), a nowe klucze ze studia mają komplet zakresów.

### Sprawdzanie opisu zatrzymało grę. Dlaczego?

Odmowa zawsze podaje słowo, które ją spowodowało. Opis sprawdzamy w języku każdego znacznika (``, ``), a słowa gatunku, jak strzał w Statkach czy strzelanie kulką, nie wymagają zaznaczenia przemocy w ankiecie. Przemoc to zabijanie, krew, broń i gatunek strzelanki.

### Jak usunąć paczkę z poczekalni?

`klyo_delete_game` z `upload_id` zamiast `slug`. Paczka, z której powstała już gra, zostaje, bo jest podglądem tej gry.

### Bramka pisze „wyjątki”, a gra działa. Co to znaczy?

Wyjątek to błąd JavaScriptu zgłoszony przez przeglądarkę. Meldunki stanu gry (`stan:`) i dziennik nagrywania (`obraz:`, `kompozyt:`) wyjątkami nie są i wydania nie zatrzymują. Wynik wysyłany przez zestaw trzymany w zmiennej też się liczy: podgląd melduje wtedy „gra wysłała wynik”.

### Czy gry online przetrwają zerwane połączenie?

Tak. Każdy ruch ma numer i własny identyfikator. Gdy telefon na chwilę straci sieć, strona po powrocie dociąga ruchy, które ominęły gracza, raz i w kolejności, a ruch wysłany w złej chwili ponawia się sam, bez dublowania. Szybki mecz sam dobiera przeciwnika, a „Wyjdź z pokoju” naprawdę zamyka pokój.

### Odpowiedź narzędzia jest za duża dla asystenta. Co zrobić?

Użyj `limit`. `klyo_ads_ideas` oddaje najpopularniejsze frazy (domyślnie 50, z liczbą wszystkich), a z `tylko_zarodki` tylko podane frazy z liczbami. `klyo_keyword_map` skraca listy do 40 i liczy stan z całości. `klyo_my_games` niesie przy grze sam wyrok nagrania, bez pomiarów.

### Czy mogę zmierzyć grę w wybranych językach?

Tak. `klyo_game_diagnostics` z `zmierz`, `pelny` i `jezyki: ["pl","en","de"]` sprawdza dokładnie te języki, razem ze słabym telefonem. Drugi pomiar zamówiony w czasie pierwszego czeka w kolejce i rusza sam.

### Czy muszę używać asystenta?

Nie. Wszystko, co robi narzędzie, zrobisz w przeglądarce na [dev.klyo.pl](https://dev.klyo.pl/): wybierasz paczkę, od razu widzisz grę w oknie i uzupełniasz opis.

---

Źródło: https://games.klyo.pl/pl/mcp/ · Wykonawca: klyo software house (Łódź, cała Polska) · Kontakt: kontakt@klyo.pl · Indeks dla modeli językowych: https://games.klyo.pl/llms.txt
