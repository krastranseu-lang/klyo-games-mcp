> **Strona kanoniczna:** https://games.klyo.pl/pl/wsparcie/tablica-wynikow/ · aktualizacja 2026-09-24 · Plik powstaje automatycznie ze strony klyo games, więc poprawki wprowadzamy na stronie.

# Jak dodać tablicę wyników do gry HTML5

Dodaj skrypt zestawu klyo do pliku index.html, wywołaj klyo.ready(), gdy gra jest gotowa, klyo.progress() w trakcie partii i klyo.score() na końcu. Ustaw w studiu najwyższy możliwy wynik, a gra dostanie tablice dnia, tygodnia i wszech czasów.

## Zanim zaczniesz

- Gra wydana na klyo games albo gotowa do wgrania.
- Dostęp do pliku index.html gry. Po twojej stronie nie potrzeba serwera, bazy danych ani kont.
- Albo asystent AI podłączony przez MCP: powiedz mu, żeby dodał do gry tablicę wyników klyo.

## Krok po kroku

1. **Dodaj zestaw**: Wstaw tę linijkę do pliku index.html przed własnym skryptem: ``. Otwarta poza klyo gra działa dalej, a wyniki zostają po prostu w przeglądarce.
2. **Powiedz stronie, że gra jest gotowa**: Wywołaj `klyo.ready()`, gdy gra się wczyta i da się w nią grać. Strona chowa wtedy zasłonę wczytywania.
3. **Zgłaszaj postęp w trakcie partii**: Wywołuj `klyo.progress(punkty)` przy każdej zmianie wyniku. Zestaw wysyła najwyżej cztery zmiany na sekundę, a strona pokazuje graczowi pod grą cel, na przykład miejsce 14 i liczbę punktów do następnego gracza.
4. **Wyślij wynik końcowy**: Na końcu partii wywołaj `klyo.score(punkty, odpowiedz)`. Odpowiedź niesie miejsce dnia, tygodnia i wszech czasów oraz gracza tuż przed tobą, gotowe na ekran końca. Liczy się jeden najlepszy wynik na urządzenie dziennie.
5. **Ustaw limit wyniku**: W studiu, przy opisie gry, wypełnij pole „Najwyższy możliwy wynik w jednej partii”. Wyniki powyżej odpadają od razu, a kafelek gry w centrum rekordów dostaje znak limitu. Bez limitu wynik dziesięć razy wyższy od kolejnego czeka na sprawdzenie.
6. **Pokaż tablicę w grze (opcjonalnie)**: `klyo.leaderboard.get("day", odpowiedz)` oddaje 20 najlepszych wyników dnia, tygodnia albo wszech czasów, z tymi samymi imionami graczy co w społeczności.

## Jeśli coś nie działa

### Wyniki się nie pojawiają

Wynik liczy się dopiero po partii trwającej co najmniej 3 sekundy i tylko wtedy, gdy gra działa na klyo. Sprawdź, czy zestaw wczytuje się przed twoim skryptem i czy wywołujesz klyo.ready().

### Wynik został odrzucony

Jest powyżej ustawionego limitu albo przyszedł za szybko po poprzednim wyniku z tego samego urządzenia.

### Gracze pytają, gdzie jest tablica

Stoi sama na stronie gry i w centrum rekordów. W samej grze rysujesz ją tylko wtedy, gdy wywołasz klyo.leaderboard.get.

## Częste pytania

### Czy gracz potrzebuje konta do tablicy wyników?

Nie. Wynik należy do urządzenia; z kontem na tablicy stoi imię gracza, a wynik idzie za nim na jego inne urządzenia.

### Czy da się oszukać tablicę z konsoli przeglądarki?

Nie. Wynik przechodzi tylko z żetonem, który serwer podpisuje przy starcie partii, po co najmniej 3 sekundach gry i poniżej twojego limitu, więc wpisanie liczby w konsoli nic nie da.

## Powiązane instrukcje

- [Jak wydać grę HTML5 na klyo games](https://games.klyo.pl/pl/wsparcie/jak-wydac-gre-html5/)
- [Jak wydać nową wersję gry i wrócić do poprzedniej](https://games.klyo.pl/pl/wsparcie/nowa-wersja-gry/)
- [Gra pokazuje białe okno: jak to naprawić](https://games.klyo.pl/pl/wsparcie/biale-okno/)
- [Wszystkie instrukcje](https://games.klyo.pl/pl/wsparcie/)

Nadal coś nie działa? Napisz na [kontakt@klyo.pl](mailto:kontakt@klyo.pl) i podaj adres gry. Odpowiada człowiek, w dwa dni robocze.

---

Źródło: https://games.klyo.pl/pl/wsparcie/tablica-wynikow/ · Autor: klyo, polska firma technologiczna (Łódź, klienci w całej Polsce) · Kontakt: kontakt@klyo.pl · Indeks dla modeli językowych: https://games.klyo.pl/llms.txt
