> **Strona kanoniczna:** https://games.klyo.pl/pl/zestaw-do-gry/ · aktualizacja 2026-09-24 · Plik powstaje automatycznie ze strony klyo games, więc poprawki wprowadzamy na stronie.

# Zestaw klyo dla gry HTML5

Jeden plik dołączony do gry i twoja gra umie rozmawiać ze stroną, na której stoi: wysyła wynik na tablicę, zapisuje postęp gracza na serwerze, prosi o przerwę reklamową i pozwala nagrać klip. Gra nie dostaje dostępu ani do strony, ani do reklam, ani do serwera. Prosi, a strona decyduje.

## Jak dołączyć zestaw do gry

Jedna linia w pliku index.html, przed twoim skryptem. Zestaw działa też wtedy, gdy ktoś otworzy grę poza katalogiem: wywołania nie wywalają się, tylko odpowiadają natychmiast. Nazwy są angielskie (twórcy są z całego świata); polskie nazwy z wcześniejszych wersji (klyo.gotowa, klyo.wynik, klyo.postep, klyo.tablica, klyo.zapis, klyo.przerwa, klyo.nagroda, klyo.pelnyEkran, klyo.obraz) działają dalej, bo to te same funkcje.

``

## Jak zgłosić, że gra jest gotowa do grania

Wywołaj to, gdy gra się wczytała i da się w nią grać. Strona chowa wtedy zasłonę ładowania i przestaje pokazywać kręcące się kółko.

`klyo.ready();`

## Jak wysłać wynik gracza na tablicę

Po każdej skończonej partii. Wynik trafia na tablicę na serwerze i do rekordów gracza, także wtedy, gdy zagra na drugim urządzeniu, jeśli ma konto. Odpowiedź niesie wszystko na ekran końca: pozycję dziś ze skokiem, w tygodniu, od zawsze i gracza tuż nad.

`klyo.score(1200, (o) => {
// o.todayRank, o.previousTodayRank (skok),
// o.weekRank, o.allTimeRank,
// o.above = { name, score } → „320 do OpenGamers”
pokazEkranKonca(o);
});`

## Jak dać graczowi cel w trakcie partii

Wołaj przy każdej zmianie wyniku, a zestaw sam trzyma tempo (do 4 razy na sekundę). Strona pokazuje pod grą żeton „#14 · 320 do OpenGamers”, a przy mijaniu „↑ #13, wyprzedzasz…”. Bez tego wywołania żetonu nie ma; nic nie idzie do sieci, to rozmowa ze stroną.

`klyo.progress(punkty);`

## Jak pokazać dwadzieścia najlepszych wyników

Trzy okresy: day, week, all. Odpowiedź zawiera podpisy graczy, te same, które widać w społeczności.

`klyo.leaderboard.get("day", (t) => {
pokazTablice(t.entries);
});`

## Jak zapisać postęp gracza między urządzeniami

Do 64 KB na gracza i grę, po stronie serwera. Wczytaj na starcie, zapisuj po ważnych zmianach, nie po każdej klatce.

`klyo.save.set({ poziom: 4, zloto: 120 });
klyo.save.get((z) => {
if (z.ok && z.data) wczytajStan(z.data);
});`

## Jak wstawić przerwę reklamową w dobrym miejscu

Ty wybierasz moment, nie my. Dobre miejsca to koniec poziomu i ekran po przegranej; złe to środek walki. Gra czeka na wywołanie zwrotne, zanim ruszy dalej.

`klyo.adBreak("between-levels", () => {
wznowGre();
});`

## Jak dać reklamę za nagrodę

Gracz sam ją włącza przyciskiem: „obejrzyj i zgarnij bonus”. Nagrodę dajesz WYŁĄCZNIE wtedy, gdy odpowiedź ma ok równe prawda; fałsz znaczy, że reklamy nie było, nie dobiegła końca albo gracz ją zamknął.

`przyciskBonus.onclick = () => {
klyo.rewardedAd((o) => {
if (o.ok) dajBonus(500);
else powiedz("Bonus następnym razem.");
});
};`

## Jak poprosić o pełny ekran

Przeglądarki wpuszczają na pełny ekran tylko w odpowiedzi na kliknięcie gracza, więc wywołaj to z obsługi kliknięcia, a nie po wczytaniu gry.

`klyo.fullscreen();`

## Jak pozwolić graczowi nagrać klip z twojej gry

Jedna linia i gracz ma na stronie działający przycisk nagrywania. Klatki nie przechodzą przez granicę okien: gra koduje je u siebie i oddaje gotowe bajty, dlatego działa to także na telefonie, gdzie nagrywania ekranu w przeglądarce nie ma.

`klyo.canvas(mojePlotno);`

## Jak zareagować, gdy strona prosi o ciszę

Gracz gra w małym oknie przy biurku i wycisza portal. Strona nie może uciszyć twojej gry z zewnątrz (przeglądarka na to nie pozwala), więc mówi ci o tym, a ty decydujesz: wyciszasz miksera, zatrzymujesz muzykę. Bez tego wywołania nic się nie dzieje i nic się nie psuje.

`klyo.onSound((on) => {
mikser.mute = !on;
});`

## Jak dobrać sterowanie do urządzenia

Dotyk czy klawiatura, ile pikseli, bez zgadywania po szerokości ekranu. Odpowiedź: { touch, width, height }.

`const d = klyo.device();
if (d.touch) pokazPrzyciskiNaEkranie();`

## Jak zagrać online w kilka osób

Pokój z kodem (6 znaków) do wysłania znajomym albo szybkie kojarzenie w obrębie gry. Serwer pilnuje kolejności tur i zapisuje ruchy, a reguły sprawdza sama gra. Ruch i wiadomość mają do 1 KB, pokój na tury do 64 osób, na żywo do 16. Partię kończy move z result.winner: z tego liczy się ranking wygranych (klyo.online.ranking), a szybki mecz dobiera gracza o podobnym bilansie. Gra czasu rzeczywistego łączy graczy bezpośrednio (WebRTC) przez signal i onSignal; send to tylko zapas z limitem 20 na sekundę. Klucze odpowiedzi po angielsku: room.code, room.me, room.host, room.turn, room.players.

`klyo.online.quick((o) => {
if (o.ok) pokazKod(o.room.code);
});
klyo.online.onStart((r) => zacznij(r.players, r.turn));
klyo.online.onMove((m) => zastosuj(m.who, m.move));
// gdy klyo.online.room().turn === klyo.online.room().me:
klyo.online.move({ from: 12, to: 16 });`

## Jak dać graczom lobby bez pisania go samemu

Okno „Zagraj online” (szybki mecz z graczem o podobnym bilansie, własny pokój z kodem, link do wysłania znajomemu, lista czekających pokoi, najlepsi gracze i twój bilans) rysuje portal, nie gra. Gra woła jedno wywołanie i dostaje odpowiedź, gdy partia rusza. Link z kodem (?pokoj=KOD) otwiera stronę gry i sam dołącza; po odświeżeniu strony resume wraca do partii z listą ruchów.

`klyo.online.lobby({ players: 2 }, (o) => {
if (o.ok) zacznij(o.room);
});`

## Kompletny przykład: kółko i krzyżyk online (cały plik)

Wklej do index.html, dodaj zestaw i wydaj. Gospodarz gra krzyżykiem, serwer pilnuje, kto ma ruch, a plansza wraca po odświeżeniu.

`

var B = document.getElementById("board"), S = document.getElementById("status");
var cells = ["", "", "", "", "", "", "", "", ""], mark = "";
function me() { var r = klyo.online.room(); return r ? r.me : ""; }
function draw() { var h = ""; for (var i = 0; i ' + (cells[i] || "\u00b7") + ""; B.innerHTML = h; }
function won() { var L = [[0,1,2],[3,4,5],[6,7,8],[0,3,6],[1,4,7],[2,5,8],[0,4,8],[2,4,6]];
return L.some(function (l) { return cells[l[0]] && cells[l[0]] === cells[l[1]] && cells[l[0]] === cells[l[2]]; }); }
B.addEventListener("click", function (e) {
var i = e.target.getAttribute("data-i"), r = klyo.online.room();
if (i === null || cells[i] || !r || r.turn !== r.me) return; // serwer pilnuje, kto ma ruch; gra sprawdza reguły
cells[i] = mark; draw();
klyo.online.move({ i: +i }, won() ? { end: true, result: { winner: r.me } } : null);
});
klyo.online.onStart(function (r) { mark = r.host === me() ? "X" : "O"; cells = ["", "", "", "", "", "", "", "", ""]; draw(); S.textContent = "Gra! Ty: " + mark; });
klyo.online.onMove(function (m) { if (m.who !== me()) { cells[m.move.i] = mark === "X" ? "O" : "X"; draw(); } S.textContent = m.turn === me() ? "Twój ruch" : "Ruch przeciwnika"; });
klyo.online.onEnd(function (z) { S.textContent = z.result && z.result.winner === me() ? "Wygrana!" : "Koniec partii"; });
klyo.ready();
klyo.online.resume(function (r) { // powrót po odświeżeniu albo z linku ?pokoj=KOD
if (r.ok) { r.moves.forEach(function (m) { cells[m.move.i] = m.who === r.room.host ? "X" : "O"; }); draw(); return; }
klyo.online.lobby({ players: 2 }, function (o) { if (!o.ok) S.textContent = "Zagraj, gdy będziesz gotowy."; });
});
`

## Jak wskazać moment, który wart jest klipu

Gra wie najlepiej, kiedy dzieje się coś, co warto pokazać: combo, wybuch, przejście poziomu, przegrana o włos. Jedno wywołanie stawia znacznik na osi czasu nagrania. Edytor klipu sam zaznacza odcinek wokół ostatniego znacznika, a gracz nie szuka momentu po sekundzie. Rekord z klyo.wynik ma pierwszeństwo. Rodzaj to krótkie słowo bez spacji, dane to mały obiekt do podpisu klipu. Nic nie idzie do sieci; bez nagrywania znacznik po prostu przepada.

`klyo.moment("combo", { seria: 12 });`

## Jak zbudować grę pod rekordy

**Co gra dostaje za darmo.** Kafel na hubie rekordów (games.klyo.pl/pl/rekordy/) z rekordem od zawsze i podium, miejsce w tabeli medalowej dnia (złoto, srebro, brąz za miejsca 1–3 w każdej grze), wpis na pasku „ostatnie rekordy” na żywo, plakietkę „Dziś prowadzi X” na kaflu w katalogu i powiadomienie „X cię wyprzedził” dla graczy z kontem. Warunek jest jeden: gra woła `klyo.wynik`.

**Trzy wywołania i gotowe.** Na starcie `klyo.ready()`, w trakcie partii `klyo.progress(punkty)` (żeton „#14 · 320 do X” pod grą), na końcu `klyo.score(punkty, cb)`, a odpowiedź ma wszystko na ekran końca: pozycję dziś ze skokiem, w tygodniu, od zawsze i gracza tuż nad. Jeden najlepszy wynik na urządzenie dziennie: dziesięć partii z rzędu nie zajmuje dziesięciu miejsc.

**Próg wyniku.** W studiu, w wierszu gry, ustaw najwyższy wynik, jaki gra może dać. Kafel dostaje znak „próg ✓”, a wynik ponad próg odpada od razu. Bez progu tablica działa, ale kafel ma znak „bez progu”, a wynik ponad dziesięć razy wyższy od kolejnego (przy co najmniej dziesięciu wpisach) jest „do sprawdzenia”. Wpis możesz usunąć w Karcie gry.

**Z asystentem AI (MCP).** Podłącz klyo do swojego asystenta i powiedz: „dodaj tablicę wyników klyo do tej gry”. Narzędzie `klyo_game_sdk` daje mu ten sam opis, co tutaj: wywołania, wzorzec start → postęp → wynik, próg. Nową paczkę wysyła `klyo_update_game`.

[Instrukcja krok po kroku: tablica wyników w grze HTML5](https://games.klyo.pl/pl/wsparcie/tablica-wynikow/)

## Czego zestaw nie robi i czego nie wolno wgrać

**Gra nie może zawierać własnych reklam.** Żadnej obcej sieci: AdMob, AdSense, Unity Ads, AppLovin, ironSource, Poki, CrazyGames ani podobnych. Sito przy wgrywaniu odrzuca taką paczkę i podaje nazwę znalezionej sieci.

**Dlaczego tak.** Reklamy odtwarza nasza strona wokół ramki z grą. Dzięki temu jest jedno konto wydawcy, jedno rozliczenie i sprawdzalny udział twórcy. Dwóch wydawców na jednej stronie to dla Google nieprawidłowość karana wyłączeniem konta: naszego i pośrednio twojego.

**Gra nie sięga do strony ani do serwera.** Nie ma dostępu do ciasteczek, do konta gracza ani do danych innych gier: stoi na własnym adresie i rozmawia ze stroną wyłącznie tymi wywołaniami. Dlatego możemy przyjmować cudze gry, nie czytając ich kodu linia po linii.

**Do przetestowania przed pierwszą reklamą.** Przerwa i nagroda działają w podglądzie i na portalu także wtedy, gdy dla gracza nie ma reklamy: zamiast niej strona pokazuje krótką zaślepkę i odpowiada dokładnie tak, jak z prawdziwą reklamą, więc całą mechanikę bonusu zbudujesz i przetestujesz przed pierwszą złotówką.

## Co się dzieje, gdy ktoś otworzy grę poza klyo

Nic się nie psuje. Przerwa wraca natychmiast, wynik i zapis zostają w pamięci przeglądarki, a klip po prostu nie ma gdzie się zapisać. Możesz więc trzymać jedną wersję gry na wszystko i nie potrzebujesz osobnej paczki dla nas.

## Klyo Kit: szkielet gry na poziomie studia

Dwa znaczniki i jedno wywołanie. Kit daje to, co każde studio ma wspólne: menu, pauzę, ekran końca z rekordem i pozycją na tablicy, ustawienia (dźwięk, motyw jasny/ciemny, język), sterowanie dotykiem, myszą, klawiaturą i padem jednym zdarzeniem, płótno na dowolny ekran z wcięciami iPhone’a, dźwięk bez plików (syntezowany, z wznowieniem po powrocie z tła), „juice” (tweeny, drżenie, cząsteczki, błysk), zapis między urządzeniami, tryby: sam, na jednym urządzeniu (oddaj telefon), online na link. Ty piszesz tylko rozgrywkę.

`

var gra = klyoKit.start({ nazwa: "Moja gra", tryby: ["solo", "hotseat", "online"], uklad: "oba",
naStart: function (tryb) { nowaPartia(); } });
var c = gra.plotno(), g = c.getContext("2d"); // cały ekran, DPR, resize
gra.on("tap", function (d) { /* dotyk i mysz razem */ gra.dzwiek.graj("zbior"); gra.juice.czastki(d.x, d.y); });
gra.koniec({ wygrana: true, wynik: 120 }); // ekran końca + tablica + rekord
`

- **Gry referencyjne na kicie:** [Statki](https://klyo.pl/pl/statki/) (solo, na jednym urządzeniu, online na link, ~200 linii), [Czwórki](https://klyo.pl/pl/czworki/) (przeciwnik z `gra.ai.minimax`, ~110 linii), [Air Hockey](https://klyo.pl/pl/air-hockey/) (dwa palce na jednym ekranie, ~60 linii). Reszta jest w kicie.
- **Przez asystenta:** `klyo_game_scaffold` zwraca pliki-startery i pełne API; asystent nie pisze menu, pauzy ani dźwięku drugi raz.
- **Bez zewnętrznych arkuszy i czcionek:** hosty gier mają `style-src 'self'`, więc kit ma CSS wbudowany, czcionka systemowa, kolory z `gra.motyw.paleta`.

## Gra na każdym ekranie: czego wymagamy i co mierzymy

Gra dostaje u nas cały prostokąt sceny, a w pełnym ekranie cały ekran urządzenia: na telefonie „Zagraj” otwiera pełny ekran w tym samym geście, gra pozioma na pionowym telefonie dostaje ramkę obróconą o 90°, a żaden gest nie idzie do przeglądarki. Gra musi więc układać się do dowolnych proporcji, od 390×844 do 2400×1560.

- **Układ do dowolnych proporcji.** Nasłuchuj `resize`, skaluj płótno do `innerWidth × innerHeight`; żadnego sztywnego 1280×720 z pasami.
- **Dotyk.** `pointerdown/pointermove` albo `touchstart/touchmove` z `{ passive: false }` i `preventDefault()` na płótnie oraz `touch-action: none`. Sterowanie dotykiem to stuknięcie i przeciągnięcie. Na telefonie nie ma najechania kursorem, więc celowanie „przy ruchu bez przycisku” tam nie istnieje. Gra bez nasłuchu dotyku dostaje w studiu zadanie „tylko komputer”.
- **Czytelność.** Najmniejszy tekst ≥ 10 px CSS przy szerokości 390 px i przy devicePixelRatio 1.
- **Układ przy wydaniu.** Zadeklaruj poziom, pion albo oba, a portal sam prosi o obrót i obraca ramkę; nie blokuj orientacji w grze.
- **Dźwięk.** Start po pierwszym geście gracza; po powrocie z tła (iPhone) wznów AudioContext w geście.
- **Waga i czas.** Pierwsze pobranie ≤ 20 MB na telefon, pierwsza klatka gry ≤ 20 s, ścieżki względne.
- **Sprawdź u siebie, zanim wgrasz.** `node klyo-test.mjs http://localhost:8080/ moja-gra ./klyo-test --uklad=pion`. Plik [/sdk/klyo-test.mjs](https://games.klyo.pl/sdk/klyo-test.mjs) mierzy dokładnie to, co my przy publikacji, z tymi samymi progami (Node 22 + Chrome/Chromium); `--uklad` to układ, który zadeklarujesz przy wydaniu (pion | poziom | oba). Przed wydaniem dodaj `--slaby-telefon --jezyki`: tani telefon (procesor cztery razy wolniejszy, słaba sieć) oraz ta sama gra po polsku i po angielsku, z miniaturą każdego języka.

Przy publikacji otwieramy grę w czterech ekranach (telefon w pionie i w poziomie z dotykiem, tablet, komputer) i mierzymy: przewijanie w ramce, ułamek ekranu zajęty przez grę, najmniejszy tekst, nasłuchy dotyku, wagę pierwszego pobrania i czas wczytania. Wynik z miniaturami widzisz w Karcie gry w studiu, a twój asystent w klyo_game_diagnostics. Sami nie zgadujemy: to samo widzi gracz.

## Czego wymagamy od paczki

- Plik **index.html** w katalogu głównym paczki ZIP. Od niego zaczyna się gra.
- Gra ma działać **bez instalacji i bez konta**, w przeglądarce, także na telefonie.
- Do 100 MB. Sito sprawdza rozmiar, brakujące pliki, obce sieci reklamowe i ślady złośliwego kodu w kilkanaście sekund.
- Ankieta wieku wypełniana przy wgrywaniu daje etykietę, która decyduje o widoczności i o wejściu do aplikacji sklepowych.

---

Źródło: https://games.klyo.pl/pl/zestaw-do-gry/ · Autor: klyo, polska firma technologiczna (Łódź, klienci w całej Polsce) · Kontakt: kontakt@klyo.pl · Indeks dla modeli językowych: https://games.klyo.pl/llms.txt
