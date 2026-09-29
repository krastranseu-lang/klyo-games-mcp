> **Canonical page:** https://games.klyo.pl/game-sdk/ · updated 2026-09-29 · This file is generated from the klyo games website, so changes are made on the website.

# klyo SDK for HTML5 games

One file added to your game and it can talk to the page it runs on: it sends scores to a leaderboard, saves progress on our server, asks for an ad break and lets the player record a clip. The game gets no access to the page, to ads or to the server. It asks, and the page decides.

## How to add the SDK to your game

One line in index.html, before your own script. It also works when somebody opens the game outside the catalogue: calls do not break, they answer immediately. The Polish names from earlier versions (klyo.gotowa, klyo.wynik, klyo.postep, klyo.tablica, klyo.zapis, klyo.przerwa, klyo.nagroda, klyo.pelnyEkran, klyo.obraz) keep working, because they are the same functions.

``

## How to report that the game is ready to play

Call this once the game has loaded and can be played. The page then hides the loading cover and stops the spinner.

`klyo.ready();`

## How to send a score to the leaderboard

After every finished round. The score goes to the server leaderboard and to the player's records, including on a second device if they have an account. The answer carries everything for the end screen: today's position with the jump, this week's, all-time and the player just above.

`klyo.score(1200, (o) => {
// o.todayRank, o.previousTodayRank (jump),
// o.weekRank, o.allTimeRank,
// o.above = { name, score } → "320 to OpenGamers"
showEndScreen(o);
});`

## How to give the player a goal during the round

Call it on every score change; the kit throttles itself (up to 4 times a second). The page shows a token under the game: “#14 · 320 to OpenGamers”, and “↑ #13, you pass…” when passing someone. Without this call there is no token; nothing goes to the network, it is a conversation with the page.

`klyo.progress(points);`

## How to show the twenty best scores

Three periods: day, week, all. The answer carries player names, the same ones the community shows.

`klyo.leaderboard.get("day", (t) => {
showBoard(t.entries);
});`

## Teams, maps and one-link invites

You pass teams and maps to the lobby, and the room on the server keeps them: the portal lobby shows team columns with free spots (the player picks, a full team says no) and map tiles (the host picks). An invite link takes a friend straight into the room and into the team of whoever sent it, so you play together. On a computer opening the link is enough, on a phone one tap on the invite card. Quick match picks by map and team, and with dropIn it puts players straight into a running match. Set sides and the map only from room().players[i].team and room().map, never from a local choice in your game menu: that way two players who both picked attack are sure to end up in one team.

`klyo.online.onInvite(() => playOnline()); // player from a link
function playOnline() {
klyo.online.lobby({ players: 10, mode: "realtime", dropIn: true,
teams: [{ id: "attack", name: "Attack" }, { id: "defense", name: "Defense" }],
maps: [{ id: "port", name: "Port", image: "maps/port.webp" }] }, (o) => {
if (!o.ok) return;
const me = o.room.players.find((p) => p.who === o.room.me);
startMatch(o.room.map, me.team, o.room.players);
});
}`

## How the server guards match rules

You write the match rules into a klyo-rules.json file in your package: how many times per second a player may shoot, how many rounds a magazine holds, what refills it and how long a reload takes, how fast a character moves and the highest damage. We read the file at release, so a player cannot change it in the browser. The match server checks every action before other players see it, on the fallback connection too. A broken rule reaches nobody, and your game gets onReject with the reason. Take hits and points only from messages that carry an action.

`klyo.online.act("shoot", { damage: 36, hit: target });
klyo.online.pos(x, y, z);
klyo.online.onReject((r) => {
// r.reason: "burst-empty", "locked", "too-fast", "too-far"
fixAmmo(r);
});
// klyo-rules.json:
// { "online": { "actions": { "shoot": { "perSecond": 10, "burst": 30, "refill": "reload" },
// "reload": { "lockMs": 2500 } }, "position": { "maxSpeed": 7.5 } } }`

## How to show the weekly tournament

Every game with the SDK gets a tournament on its own: Monday to Sunday, no cash prizes, the podium earns XP (100, 60 and 30) when at least three players took part. Only scores that passed the fairness check enter the table. The answer has the edition end, the top 50, your place and the winners of recent weeks.

`klyo.tournament.get((t) => {
// t.endsAt, t.entries, t.me = { rank, score },
// t.winners = [{ edition, name, score }]
showTournament(t);
});`

## How to save progress across devices

Up to 64 KB per player and game, stored on the server. Load at start, save after meaningful changes, not every frame.

`klyo.save.set({ level: 4, gold: 120 });
klyo.save.get((z) => {
if (z.ok && z.data) loadState(z.data);
});`

## How to place an ad break where it belongs

You choose the moment, not us. Good places are the end of a level and the screen after a loss; a bad one is the middle of a fight. The game waits for the callback before it moves on.

`klyo.adBreak("between-levels", () => {
resumeGame();
});`

## How to add a rewarded ad

The player turns it on with a button: watch and collect a bonus. Grant the reward ONLY when the answer has ok set to true; false means there was no ad, it did not finish, or the player closed it.

`bonusButton.onclick = () => {
klyo.rewardedAd((o) => {
if (o.ok) giveBonus(500);
else say("Bonus next time.");
});
};`

## How to request full screen

Browsers allow full screen only in response to a player's click, so call this from a click handler, not after the game loads.

`klyo.fullscreen();`

## How to let players record a clip of your game

One line and the player gets a working record button on the page. Frames never cross the window boundary: the game encodes them itself and hands over finished bytes, which is why this also works on phones, where browsers have no screen recording.

`klyo.canvas(myCanvas);`

## How to react when the page asks for silence

A player runs the game in a small window at a desk and mutes the portal. The page cannot silence your game from outside (the browser forbids it), so it tells you, and you decide: mute the mixer, stop the music. Without this call nothing happens and nothing breaks.

`klyo.onSound((on) => {
mixer.mute = !on;
});`

## How to adapt controls to the device

Touch or keyboard, how many pixels, without guessing from screen width. The answer: { touch, width, height }.

`const d = klyo.device();
if (d.touch) showOnScreenButtons();`

## How to play online with several people

A room with a 6-character code to send to friends, or quick matching within the game. The server keeps turn order and stores the moves, and the game checks the rules. A move or message is up to 1 KB, a turn-based room up to 64 people, a live one up to 16. A match ends with move and result.winner, which feeds the wins ranking (klyo.online.ranking), and quick match pairs players with a similar record. In a live room (mode: 'realtime') send and onMessage travel over a UDP channel to the klyo match server, up to 120 messages a second; send bytes (Uint8Array), a string or an object of up to about 1 KB and the receiver gets the same type. A send message can be lost on the way like any UDP packet, so use it for state that refreshes anyway. For an event that must arrive (a shot, a hit, a pickup), use klyo.online.act, also in a game without rules: the SDK sends it three times and the receiver gets it once. klyo.online.net() tells you the transport and the ping. If UDP does not get through, the same calls use a backup connection (20 per second). Response keys: room.code, room.me, room.host, room.turn, room.players.

`klyo.online.quick((o) => {
if (o.ok) showCode(o.room.code);
});
klyo.online.onStart((r) => begin(r.players, r.turn));
klyo.online.onMove((m) => apply(m.who, m.move));
// when klyo.online.room().turn === klyo.online.room().me:
klyo.online.move({ from: 12, to: 16 });`

## How to give players a lobby without writing one

The “Play online” window (quick match with a player of a similar record, your own room with a code, a link to send a friend, a list of waiting rooms, top players and your record) is drawn by the portal, not by the game. The game makes one call and gets the answer when the match starts. A link with the code (?pokoj=CODE) opens the game page and joins by itself; after a page refresh, resume returns to the match with the list of moves.

`klyo.online.lobby({ players: 2 }, (o) => {
if (o.ok) begin(o.room);
});`

## Complete example: online tic-tac-toe (whole file)

Paste into index.html, add the SDK and publish. The host plays X, the server keeps whose turn it is, and the board comes back after a refresh.

`

var B = document.getElementById("board"), S = document.getElementById("status");
var cells = ["", "", "", "", "", "", "", "", ""], mark = "";
function me() { var r = klyo.online.room(); return r ? r.me : ""; }
function draw() { var h = ""; for (var i = 0; i ' + (cells[i] || "\u00b7") + ""; B.innerHTML = h; }
function won() { var L = [[0,1,2],[3,4,5],[6,7,8],[0,3,6],[1,4,7],[2,5,8],[0,4,8],[2,4,6]];
return L.some(function (l) { return cells[l[0]] && cells[l[0]] === cells[l[1]] && cells[l[0]] === cells[l[2]]; }); }
B.addEventListener("click", function (e) {
var i = e.target.getAttribute("data-i"), r = klyo.online.room();
if (i === null || cells[i] || !r || r.turn !== r.me) return; // the server keeps whose turn it is; the game checks the rules
cells[i] = mark; draw();
klyo.online.move({ i: +i }, won() ? { end: true, result: { winner: r.me } } : null);
});
klyo.online.onStart(function (r) { mark = r.host === me() ? "X" : "O"; cells = ["", "", "", "", "", "", "", "", ""]; draw(); S.textContent = "Playing! You: " + mark; });
klyo.online.onMove(function (m) { if (m.who !== me()) { cells[m.move.i] = mark === "X" ? "O" : "X"; draw(); } S.textContent = m.turn === me() ? "Your move" : "Opponent's move"; });
klyo.online.onEnd(function (z) { S.textContent = z.result && z.result.winner === me() ? "You win!" : "Match over"; });
klyo.ready();
klyo.online.resume(function (r) { // return after a refresh or from a ?pokoj=CODE link
if (r.ok) { r.moves.forEach(function (m) { cells[m.move.i] = m.who === r.room.host ? "X" : "O"; }); draw(); return; }
klyo.online.lobby({ players: 2 }, function (o) { if (!o.ok) S.textContent = "Play when you are ready."; });
});
`

## How to mark a moment worth a clip

The game knows best when something worth showing happens: a combo, an explosion, a level cleared, a loss by a hair. One call puts a marker on the recording timeline. The clip editor selects the stretch around the last marker by itself, so the player does not hunt for the moment second by second. A record from klyo.wynik takes precedence. The kind is a short word without spaces, the data a small object for the clip caption. Nothing goes to the network; without a recording the marker simply expires.

`klyo.moment("combo", { streak: 12 });`

## Shared weekly competition — API 1.2.0

The edition changes automatically on Monday at 00:00 UTC. The server calculates scores from moves and records the best completed attempt. Ordinary game records remain separate.

The owner must first enable an installed rules module for the game. Available now: blockfall-weekly-v1. Another game requires its own server rules module.

`klyo.league.standings({scope: 'week'}, showBoard);
klyo.league.start(crypto.randomUUID(), resumeRun);
// Keep run and base; retry identical moves after a lost acknowledgement.
klyo.league.moves(run, base, [column], acceptServerState);
klyo.league.finish(run, moveCount, showConfirmedScore);`
Ordinary records: standings({scope:"classic"}). These are client-reported, not replay-verified. record({}) returns a profile and requiredConsent. Explicit publication requires {score, gameRank, publish:true, consentVersion:requiredConsent, eligible16:true}; never set consent automatically. record({score,gameRank}) only updates an existing public entry. record({publish:false}) withdraws publication without changing the private game save. data and erase cover both boards.

| SDK | RPC v1 | Arguments |
| --- | --- | --- |
| `klyo.league.standings` | `gry.liga.tablica.v1` | options, callback |
| `klyo.league.start` | `gry.liga.start.v1` | requestId string or {requestId, gameRank?}, callback |
| `klyo.league.moves` | `gry.liga.ruchy.v1` | run, base, columns, callback |
| `klyo.league.finish` | `gry.liga.koniec.v1` | run, moves, callback |
| `klyo.league.data` | `gry.liga.dane.v1` | options, callback |
| `klyo.league.erase` | `gry.liga.usun.v1` | confirm, callback |
| `klyo.league.record` | `gry.liga.rekord.v1` | options, callback |

Identity comes from the authenticated Klyo host or verified Facebook proof. Provider accounts are not automatically linked. Future Klyo Games apps can use the same SDK bridge; this release does not ship a native mobile host.

Data export is paginated in batches of 10 runs (next cursor); deletion requires confirm: "DELETE". Runs: 90 days, weekly editions: 52 weeks, all-time competitive best: until deletion. On SERVER_BUSY retry after a delay with the same operation identifier.

## How to build a game for the records hub

**What the game gets for free.** A tile on the records hub (games.klyo.pl/records/) with the all-time record and podium, a place in the medal table of the day (gold, silver, bronze for places 1–3 in every game), an entry on the live “latest records” strip, a “Today's leader: X” badge on the catalogue tile and a “X passed you” notification for players with an account. One condition: the game calls `klyo.wynik`.

**Three calls and done.** On start `klyo.ready()`, during the round `klyo.progress(points)` (the “#14 · 320 to X” token under the game), at the end `klyo.score(points, cb)`, and the answer has everything for the end screen: today's position with the jump, this week's, all-time and the player just above. One best score per device per day: ten rounds in a row do not take ten places.

**Score cap.** In the studio, in the game's row, set the highest score the game can produce. The tile gets a “cap ✓” mark and any score above the cap is rejected on the spot. Without a cap the board works, but the tile says “no cap”, and a score more than ten times higher than the next one (with at least ten entries) is “under review”. You can remove an entry in the game card.

**With an AI assistant (MCP).** Connect klyo to your assistant and say: “add the klyo leaderboard to this game”. The `klyo_game_sdk` tool gives it the same description as this page: the calls, the start → progress → score pattern, the cap. `klyo_update_game` uploads the new package.

[Step-by-step guide: add a leaderboard to an HTML5 game](https://games.klyo.pl/support/add-leaderboard/)

## What the SDK does not do, and what you must not upload

**Your game must not carry its own ads.** No third-party network: AdMob, AdSense, Unity Ads, AppLovin, ironSource, Poki, CrazyGames or similar. The upload check rejects such a package and names the network it found.

**Why.** Ads are played by our page around the game frame. That keeps one publisher account, one settlement and a share you can verify. Two publishers on one page is, to Google, invalid traffic punished by shutting the account down: ours, and indirectly yours.

**The game does not reach the page or the server.** No cookies, no player account, no data from other games: it runs on its own address and talks to the page through these calls only. That is why we can accept other people's games without reading their code line by line.

**Testable before the first ad.** Ad breaks and rewarded ads work in the preview and on the portal even when no ad is available for a player: instead of a real ad the page shows a short stand-in screen and then answers exactly as it will with a real one, so you can build and test the whole bonus mechanic before the first cent.

## What happens when somebody opens the game outside klyo

Nothing breaks. An ad break returns at once, scores and saves stay in the browser, and a clip simply has nowhere to go. You can keep one build for everything; you do not need a separate package for us.

## Klyo Kit: a studio-grade game skeleton

Two script tags and one call. The kit provides what every studio shares: menu, pause, end screen with best score and leaderboard position, settings (sound, light/dark theme, language), touch, mouse, keyboard and gamepad as one event, a canvas for any screen with iPhone safe areas, synthesized sound without files (resuming after the background), “juice” (tweens, shake, particles, flash), cross-device save, modes: solo, same device (pass the phone), online by link. You write only the gameplay.

`

var gra = klyoKit.start({ nazwa: "My game", tryby: ["solo", "hotseat", "online"], uklad: "oba",
naStart: function (tryb) { newRound(); } });
var c = gra.plotno(), g = c.getContext("2d"); // full screen, DPR, resize
gra.on("tap", function (d) { /* touch and mouse together */ gra.dzwiek.graj("zbior"); gra.juice.czastki(d.x, d.y); });
gra.koniec({ wygrana: true, wynik: 120 }); // end screen + leaderboard + best
`

- **Reference game on the kit:** [Battleship](https://games.klyo.pl/statki/) (solo, same device, online by link, ~200 lines). `gra.ai.minimax` gives turn-based games an opponent, and `gra.wskazniki` handles several fingers on one screen. The rest is the kit.
- **Through an assistant:** `klyo_game_scaffold` returns starter files and the full API; the assistant never writes a menu, pause or audio twice.
- **No external stylesheets or fonts:** game hosts have `style-src 'self'`, so the kit embeds its CSS, uses the system font, colours come from `gra.motyw.paleta`.

## The game on every screen: what we require and what we measure

Your game gets the whole scene rectangle, and in full screen the whole device screen: on a phone “Play” opens full screen in the same gesture, a landscape game on a portrait phone gets a frame rotated by 90°, and no gesture goes to the browser. So the game must lay itself out to any aspect ratio, from 390×844 to 2400×1560.

- **Layout for any aspect ratio.** Listen to `resize`, scale the canvas to `innerWidth × innerHeight`; no fixed 1280×720 with bars.
- **Touch.** `pointerdown/pointermove` or `touchstart/touchmove` with `{ passive: false }` and `preventDefault()` on the canvas plus `touch-action: none`. Touch control is tap and drag. There is no hover on a phone, so aiming “on move without a button” does not exist there. A game without touch listeners gets a “computer only” task in the studio.
- **Legibility.** Smallest text ≥ 10 px CSS at 390 px width and at devicePixelRatio 1.
- **Layout at release.** Declare landscape, portrait or both, and the portal asks to rotate and rotates the frame; do not lock orientation in the game.
- **Audio.** Start after the first player gesture; after returning from the background (iPhone) resume the AudioContext in a gesture.
- **Size and time.** First download ≤ 20 MB on phones, first frame of the game ≤ 20 s, relative paths.
- **Check on your machine before uploading.** `node klyo-test.mjs http://localhost:8080/ my-game ./klyo-test --uklad=pion`. The file [/sdk/klyo-test.mjs](https://games.klyo.pl/sdk/klyo-test.mjs) measures exactly what we measure at release, with the same thresholds (Node 22 + Chrome/Chromium); `--uklad` is the layout you will declare at release (pion | poziom | oba). Before a release add `--slaby-telefon --jezyki`: a cheap phone (processor four times slower, weak network) and the same game in Polish and in English, with a thumbnail of each language.

On release we open the game on four screens (phone portrait and landscape with touch, tablet, computer) and measure: scrolling inside the frame, the fraction of the screen the game covers, the smallest text, touch listeners, the size of the first download and the loading time. You see the result with thumbnails in the game card in the studio, and your assistant sees it in klyo_game_diagnostics. We do not guess: this is what the player sees.

## What we require from the package

- An **index.html** file in the root of the ZIP. The game starts there.
- The game must run **without an install and without an account**, in a browser, on phones too.
- Up to 200 MB. The check looks at size, missing files, third-party ad networks and traces of malicious code, in about a dozen seconds.
- The age questionnaire filled in at upload produces the label that decides visibility and entry into the store apps.

---

Source: https://games.klyo.pl/game-sdk/ · Built and run by klyo, a Polish technology company (Łódź) · Contact: kontakt@klyo.pl · Index for language models: https://games.klyo.pl/llms.txt
