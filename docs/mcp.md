> **Canonical page:** https://games.klyo.pl/mcp/ · updated 2026-09-24 · This file is generated from the klyo games website, so changes are made on the website.

# klyo MCP server: publish HTML5 games from your AI assistant

MCP (Model Context Protocol) is the open standard AI assistants use to reach for outside tools. Here, they use it to publish games. Building a game with Claude or ChatGPT? It can publish it here on its own: it sends the package and fills in the description, and you get a finished game to look at and one button. No clicking through a form after every fix.

[**klyo**dev
**Back to the developer studio**That is where you issue the key, upload a package and release the finished game.](https://dev.klyo.pl/)

## How to connect it

1. **Accept the terms in a browser**: Go to [dev.klyo.pl](https://dev.klyo.pl/) and accept the developer terms. An assistant will not do this for you, and that is the point: a person signs the agreement.
2. **Add klyo to your assistant**: Easiest: [**connect in one click**](https://panel.klyo.pl/mcp/connect): pick your AI (Claude, ChatGPT, Gemini, Copilot, Claude Code, opencode) and we do the rest. Manually: in your assistant's settings add the tool server (MCP) at `https://panel.klyo.pl/mcp?profil=gry`. You sign in with your klyo account and decide what you agree to, the same way you connect a drive or a mailbox.
3. **Say what you want**: “Publish this game on klyo, the package is at this address” is enough. The assistant provides the ZIP address, the name, the description for players and the age questionnaire answers. Want a leaderboard and a place on the records hub? Say “add the klyo leaderboard” and the klyo_game_sdk tool describes the calls (ready → progress → score) and the score cap.
4. **Look at it and release it**: The game waits in the studio with a preview and a QR code. You play it on your phone and then press “Release to the catalogue”. Only that click puts the game in front of players.

## Your own AI in the studio, on your own plan

It works the same way as in VS Code and Cursor: the AI assistant runs on your side, under your own Claude or ChatGPT subscription, and your sign-in details stay on your device. klyo does not run the assistant on its servers and has no access to your sign-in. We receive only the finished text and publish it only after your approval.

1. **“Fill with your AI” in the New game form**: One button for the whole form. Your AI types the name, tagline, description in English and Polish, genre, controls and play time while you watch the fields fill in live. To change one field, ask in the same chat, for example “make the tagline shorter”, and the form updates right away. You tick the content survey yourself.
2. **“Translate with your AI” in the translations window**: Pick languages with the buttons in the window; the missing ones are already selected. You can add more later in the chat, for example “now German”. Every translation lands in the “Translations” window as a proposal: you check it and press “Approve”. Google only counts text a person approved.
3. **“Write with your AI” on your creator card**: Your AI writes “about me” and the tagline under your name only from your games. It shows you the text and saves it only after you agree.
4. **The window checks the connection**: After the click the window says whether your AI is connected to klyo, using the same list as the connections page. Connected: a ✓ and the “Open in Claude” or “Open in ChatGPT” button. Not connected: “Connect klyo to your AI” comes first. You do it once.

Working in Claude Code, Cursor or VS Code? Press “Copy the instruction” in the window and paste it there. The tools are the same.

## What an assistant cannot do

**Sign the agreement for you.** You accept the developer terms in a browser, on your own account. Without that the tool refuses with a clear reason, not silently.

**Release a game to the catalogue.** The assistant brings the game to the state “waiting for you”. The last step (the one after which the game is visible to people) belongs to a person.

**Tick the content survey or declarations for you.** The survey decides the age label and ads, so it is a person’s declaration. The assistant fills in the rest of the form; you click the survey.

**Touch your money.** Your bank account, settlement details and payouts are out of the tools' reach. An assistant will not see them and cannot change them.

**Skip the checks.** The package goes through the same filter as a browser upload: size, number of files, third-party ads, malicious code, profanity in the name and description, age questionnaire.

## We are in the official MCP registry

The Model Context Protocol registry is where assistants and developers look for tool servers. Getting in means proving the domain is really yours. We did it with a signed key in klyo.pl's DNS. It is not a directory you sign up to. It is one you get into.

- **You do not have to take our word for it.** The entry is public and anyone can check it, together with our server address and the page you are reading.
- **Your client can find us on its own.** Tools that read the registry will suggest klyo when you ask about publishing a game, with no address hunting.
- **The name is permanently ours.** `pl.klyo` is our namespace in the registry; nobody else can publish under it, because nobody else controls our domain.

## Other MCP servers that publish browser games

We are not the only MCP server that can publish a browser game. Here is what each one gives the game and the developer, so you can choose for yourself.

| | klyo games | Playgama | AIGameShare | Playfrog |
| --- | --- | --- | --- | --- |
| Tools for developers | 20 | 25+ | 5 | 2 |
| Sign-in | OAuth 2.1, nothing to paste | OAuth 2.1 | a token from your account pasted into the config | none; a separate management token for each game |
| Package | ZIP up to 100 MB and 5,000 files | ZIP up to 300 MB | HTML up to 2 MB or ZIP up to 30 MB | up to 2.5 MB |
| What the game gets | its own address g-.klyo.pl, a catalogue page in English and Polish, leaderboards, player clips, daily stats | a public playable link from the Playgama sandbox | a shareable link with plays, likes and a leaderboard | a shareable play link; the game has to be claimed within 7 days |
| Money for the developer | 70% of the ad revenue from the day Google AdSense approves the portal (not yet) | ads through Playgama once the game passes a session threshold; payouts from 100 USD | not stated | not stated |

Checked on 23 September 2026 in each service's own documentation: [Playgama](https://github.com/Playgama/developer-cabinet-mcp), [AIGameShare](https://www.aigameshare.com/developers), [Playfrog](https://glama.ai/mcp/connectors/games.playfrog/publish). Those services change their rules without notice; if something no longer matches, tell us and we will correct it the same day.

## What else the tools can do

| `klyo_my_games` | lists your games and their state: waiting, in the catalogue, paused, rejected with a reason |
| --- | --- |
| `klyo_publish_game` | sends the package and prepares the game for release: name, tagline, description in English and Polish, genre, content survey; the same fields and limits as the studio form |
| `klyo_game_stats` | visits and plays, day by day |
| `klyo_game_requirements` | the game production contract, the agent's first call: screens, input, game lifecycle, audio, visuals, social layer, local test, quality gate, release stages |
| `klyo_game_scaffold` | Klyo Kit, a studio-grade game skeleton: starter files and the API (menu, pause, end screen, audio, theme, input, online, hot-seat); the assistant writes only the gameplay |
| `klyo_release_rollback` | roll the game back to the previous version in one move: the previous files sit next to the current ones, nothing to upload |
| `klyo_game_diagnostics` | why the game did not start: missing files and browser errors, in order, plus the screen fit, the quality gate (critical / warnings) and, with `zmierz: true`, a measurement on request for an assistant without a browser |
| `klyo_game_files` | reads the files of your game or of a package in the waiting room: a list with hashes, a file's content, and what changed in the new version compared with the one players have |
| `klyo_game_patch` | edits your game's files without a ZIP, in a workshop next to the version players have; with `nowa` it starts a game from scratch from the Klyo Kit skeleton, with `from_upload` it adds an image, sound or font; you release it like any new version |
| `klyo_delete_game` | takes your game off the portal: the address stays yours and you can upload the game again; a second call removes it from your list for good, and the scores stay with the address |
| `klyo_fix_game` | edits the TEXT of a published game (description, how to play, round length, genre, mood) without touching the package, so no second security check |
| `klyo_game_cover` | the tile players recognise the game by: frames are shots of your running game, so the cover shows what the player will actually see |
| `klyo_game_sdk` | what a game can call here: leaderboard, progress saving, fullscreen, rewarded ad, clip. Read this BEFORE you write the game |
| `klyo_update_game` | uploads a new version of a game already in the catalogue: the package lands in the waiting room with a preview address, and the answer carries a measurement from the files: how many % of code, look and sound changed, new files and strings, the kind of change |
| `klyo_release_version` | releases the waiting version to players, the same step as “Release” in the studio; the kind of change defaults to the measurement, “what is new” with a new feature |
| `klyo_upload_package` | sends a package straight from your disk, without a public URL |
| `klyo_fill_game_form` | fills in the open “New game” form in the studio live; you watch and correct, it never touches the survey or declarations, and you publish yourself |
| `klyo_game_translate` | game text translations made by your own AI: first the original and the missing languages, then proposals you approve in the studio |
| `klyo_creator_card` | your creator card: “about me” and a tagline written from your games, saved only after you agree |
| `klyo_add_post` | a community post: a question, a call for playtests, a launch |

## Fields and rules: the same as in the studio

The assistant fills in exactly what a person clicks in the studio. Limits live in the tool schema (a gate before the call), and the server checks them again and answers with an error code that points at the field.

| Name | Up to 30 characters, as in Google Play and the App Store: just the game’s name, no tagline and no “play free online”. Not a stranger’s brand. |
| --- | --- |
| Tagline | **Required.** One sentence up to 80 characters, no full stop: what the game is, in the words players search for. It is the H2 and the title of the Google result. |
| Description | **At least 25 words**, about 220 for Google (shorter = the game page stays out of search). What you do, how a round goes, who it is for, what makes it different. Like a human: no em dashes, no “dive in”, no bullet lists. |
| Text language | `jezyk_tekstu` (pl, en, de, fr, es, pt, it, ru, uk, tr) says which language the texts are written in. **Your own AI translates the other languages** with `klyo_game_translate`, on your plan; every language goes through checks and waits in the studio for your “Approve”. `…` markers only for a version the creator really wrote. |
| Genre, shelves, mood | Genre from the list, up to three; catalogue shelves and mood optional; the lists are in the schema and come from the same file the catalogue filters by. |
| Content survey | **Ten yes/no questions** (the `ankieta` object): cartoon violence, realistic violence, fear, strong language, nudity, drugs, gambling, interaction, purchases, location access. They decide the age label, ads and the store apps. The assistant must ask the creator, not guess. |
| Age set by the creator | `wiek_min` (3, 7, 12, 16, 18) can only raise the label above the survey result, never lower it. |
| Stage | `etap`: `w_budowie`, `demo` or `gotowa`; for the first two `etap_dni` (7 or 30) sets when to remind about the decision. **The assistant must ask.** |
| Stores | `sklep_play` and `sklep_apple`: the same game’s addresses in Google Play and the App Store: badges on the game page and in share texts. |
| Controls, round, layout, score | Touch and keyboard controls (up to 300 characters), round length (up to 40), landscape/portrait/both, the highest possible score as a leaderboard guard. |

## Your own agent: a key instead of a login

Claude and ChatGPT sign in to your account themselves. If you are writing your own agent or script, you get a key and send it in a header. The same path and the same tools, without the login window.

1. **Generate a key in the studio**: At [dev.klyo.pl](https://dev.klyo.pl/), under “Server integration (API)”, press “Generate a key”. We show it once, so save it straight away. The key starts with `klyo_sk_` and you can revoke it at any moment.
2. **Send it when you connect**: The header `Authorization: Bearer klyo_sk_…` against `https://panel.klyo.pl/mcp?profil=gry`. Your agent sees exactly the tools Claude sees, not one more.
3. **Watch what the game does**: Once the preview is open, call the diagnosis. You get the files the game asked for but are missing from the package, and the errors from the browser, instead of guessing from a white screen.

### Example: asking for a diagnosis

`curl -s "https://panel.klyo.pl/mcp?profil=gry" \
-H "Authorization: Bearer klyo_sk_YOUR_KEY" \
-H "Content-Type: application/json" \
-d '{"jsonrpc":"2.0","id":1,"method":"tools/call",
"params":{"name":"klyo_game_diagnostics",
"arguments":{"slug":"lumina-thief"}}}'`

## Your browser is the eye

We run no browser farm and need none. The game runs on your machine, and our sensor inside the preview page reports what broke. Your assistant sees exactly what you would see by opening the game yourself.

1. **Open the preview yourself**: Playwright, plain Chrome or a phone via the QR code. Append `?s=your-marker` to the address (any 1–24 characters).
2. **Actually play**: Click, drag, wait for the second screen. The sensor collects exceptions, failed files, console output and whether the game started at all.
3. **Ask for the diagnosis**: `klyo_game_diagnostics` with `sesja` set to your marker. You get ONLY the errors from your run, plus the count of other people's, so nothing disappears quietly.

Order matters: asking before the game runs returns an empty answer, because there was nothing to collect.

## A package from disk, without exposing the game

Do not open a tunnel and do not put an unreleased game on public hosting. The `klyo_upload_package` tool hands the assistant an **upload pass** (a token valid for one hour that opens nothing but sending files to your account) plus the list of packages already waiting with us without a game. An assistant with a shell (Claude Code, Codex, Cursor) sends the file itself in two requests; an assistant in a chat (claude.ai, ChatGPT) asks you to drop the ZIP in the studio: the package lands in the waiting room, nothing gets published, and it picks the number from the list. The short version is below.

1. **Announce the file**: `POST /api/upload/init` with the header `Authorization: Bearer
` and `{ filename, total_size, content_type }` → you get `upload_id` and `chunk_size`.
2. **Send the bytes**: `PATCH /api/upload/` with the same pass, `Upload-Offset` and `Content-Type: application/offset+octet-stream`. Up to 32 MB in one request; bigger files in chunks. To resume, `HEAD` tells you how much we already have.
3. **Publish or update**: `klyo_publish_game` or `klyo_update_game` with `upload_id` instead of `zip_url`.

Keep the public ZIP address for a game that really is online already, for example when moving from itch.io.

## The game production standard: the assistant knows the minimum before writing code

An ordinary person tells their assistant “I want a battleship game”. An assistant connected to klyo first calls `klyo_game_requirements` and receives the contract: phone, tablet and computer; touch, mouse and keyboard; portrait and landscape reacting to resize; audio that recovers after returning from the background; save, leaderboard, pause and one-gesture retry; one palette and one style; no third-party brands and no third-party ads. It does not ask the user about any of it, it builds at that level from the start. Version 1 of the standard is frozen since 23.09.2026: a new requirement is added only when a real game on klyo runs into a real problem.

1. **Testing on the creator's machine, not on our server.** The assistant downloads `games.klyo.pl/sdk/klyo-test.mjs` and runs it locally: four screens, scrolling, screen fraction, text, touch listeners, size, time, exceptions. Before a release it adds `--slaby-telefon --jezyki`: a cheap phone and both languages. The result has `krytyczne` (critical) and `ostrzezenia` (warnings), so it fixes and re-tests in a loop until it passes. The heavy work happens on the creator's computer; klyo measures at upload and at release with the same file.
2. **Quality gate, also for packages uploaded by hand.** Every package in the waiting room is measured on four screens right after upload; `klyo_game_diagnostics` and the studio preview show the same `bramka`: exceptions, missing files, third-party ads, no SDK, no touch and scrolling block a release as “finished” (demo and “in development” pass); small screen, small text, size, no leaderboard and third-party brands need a reason.
3. **Release stages.** Local → preview (`g-podglad-…`, outside the catalogue and Google) → publication with stage `w_budowie` / `demo` / `gotowa` → a new version with its own preview while players keep the old one, the previous version stays for restore. A human approves two moments: publication and releasing a version.

## A new version of your game: through the assistant, the same as in the studio

Three steps, the same as the “New build” and “Release” buttons in the studio. The assistant does not guess what changed: we measure it from the files and tell it what that means for the clip. **You record the clip for the new version yourself**: in the studio, after the release (the recording window opens by itself for a new look or feature).

1. **Upload**: `klyo_update_game` with `slug` and `upload_id` (a file from disk) or `zip_url`. The game in the catalogue does not change right away: the new version waits in the waiting room under its own preview address. The answer: `zmiana` (code / look / sound in %, new files and strings, `podpowiedz`: poprawka | funkcja | interfejs), `adres_nowej`, `wyrok` and `dalej`.
2. **Play**: This is your check, not the assistant’s: open the preview address, ideally on your phone. The studio shows the same version in the game window with the track “version → play → release → clip”.
3. **Release**: `klyo_release_version` with `slug`; skip `zmiana` (we take the measured one) or pass it when you know better; `nowosc` is one sentence for the feed with a new feature. Before the swap the whole new version goes through the check once more. Players get it right away (whoever is playing chooses: update or finish the round), the previous one stays with us, the game page rebuilds, and we measure the screens once, after the release. Followers get a notification when the game is in the catalogue.

What it means for the clip: a poprawka (fix) keeps the clip; a funkcja (feature) keeps the clip and “what is new” goes to the feed as “New”; with an interfejs (new look) the old clip comes off the tile and the feed until you record a new one in the studio.

## Fix without a ZIP: the game workshop

Your assistant reads your game's files and edits them here, without a package from you. It works with a game in the catalogue and with a package waiting in the waiting room. Players keep the version they know until the end: the edits go to a workshop, a new version next to it with its own preview address. You release it the same way as any new version.

1. **Start from scratch if there is no game yet**: `klyo_game_patch` with `nowa` (`plansza`, `zrecznosciowa` or `logiczna`) creates a package from the Klyo Kit skeleton right in the waiting room and writes the gameplay in the same call. An assistant in a chat, with no disk and no ZIP, has its own game at a preview address from that moment.
2. **Read**: `klyo_game_files` with the game's `slug` or the package's `upload_id`. Without `path` you get the file list with a `hash` for each file, with `path` the file's content (up to 200 KB at a time, continue from `from_line`), and with `changes: true` what differs from the version players have.
3. **Edit**: `klyo_game_patch` with a list of `edits`: an exact `old_string` replaced by `new_string`, a whole file in `content`, or `delete: true`. For a file that exists you pass `expected_hash` from your read: if someone changed the file in the meantime, nothing is saved. The edits of one call go in all together or not at all. The first edit opens the workshop, and the studio shows it straight away as “New version is waiting”.
4. **Play and check**: The preview address comes back in the answer. Open it (a phone is the best test), and `klyo_game_diagnostics` shows the errors, missing files and check results of this very version, not of the one players have. An assistant without a browser passes `zmierz: true`: we open the preview for it and return the errors and thumbnails of four screens at full addresses, so it sees what the game looks like. Files unchanged since the last measurement do not start the browser again; one measurement at a time per account, six an hour.
5. **Release**: A game: `klyo_release_version` or “Release” in the studio. A package from the waiting room: `klyo_publish_game` publishes it together with the edits. Before the swap the whole game goes through the check once more.

- **The version players have does not change.** The workshop is a copy next to it and every save creates a new file, so what players download does not change for a moment.
- **Text in the conversation, files by ticket.** An edit's content writes text files (html, htm, js, mjs, css, json, svg, txt, xml, webmanifest). An image, sound, font or big file (up to 20 MB) the assistant sends with the `klyo_upload_package` ticket and passes in `from_upload`: no base64, and the start of the file has to match its extension.
- **The same check as at upload.** Every changed file is checked straight away: malicious code, third-party ads, nothing from outside klyo. A refusal saves nothing.
- **Limits.** A file up to 1 MB, one call up to 256 KB and 20 edits, three open workshops per account and one per game, up to 300 edits an hour. Releases, rollbacks and new packages up to 10 an hour: each one starts a screen measurement, and there is one measuring browser for all developers.
- **Tidiness.** A workshop with no changes for 7 days expires, and the version players have stays untouched. A preview nothing points to any more disappears after 7 days. Preview addresses stay out of Google.
- **A trail.** Every edit is written to your account's log: the file, the hash before and after, the size.
- **Undo while you work.** Before every edit we save a point `auto-N` (it is in the answer), and the assistant can name its own with `checkpoint`. `revert` goes back to any point, `discard` drops the whole workshop. This is not a release rollback: players see none of it.
- **A weak phone before release too.** At upload and at release we measure the game once more on a phone with the processor slowed down four times and a network like weak 3G: smoothness, stutters, memory and time to the first frame. Below 15 frames a second the game will not pass the gate as finished. An assistant without a browser orders the same measurement before a release: `klyo_game_diagnostics` with `zmierz` and `pelny`.
- **In every language of the game.** Klyo Kit speaks ten languages (Polish, English, German, French, Spanish, Portuguese, Italian, Russian, Ukrainian, Turkish), and the game speaks those it has its own texts for. We open the same phone in every declared language, with a thumbnail. A key instead of a word and a declared language the game does not show block the release; English in place of a translation, a sentence identical to the English one and text that does not fit its button or runs off the screen are warnings. Text drawn on a canvas you check on the thumbnails side by side.
- **Slow frames with a cause.** The frame count alone does not say whose fault it is. We measure separately the time of the game code in each frame, the browser's work and how much of the picture really changes. Slow code is `niski_fps`; light code with slow drawing is `wolne_rysowanie`, with advice on what to draw once and what every frame.
- **Security.** We open game code on our side only in an isolated browser with no access to our internal network. A game at its own address cannot act on behalf of a signed-in player either.

## Premium quality review: seven points before a release

The quality gate catches errors, but it cannot tell whether a game looks cheap. So before the assistant publishes a game as finished, or releases a new look or feature, it goes through seven points and gives evidence for each: what exactly it did. We do not judge taste and we run no model of our own. We match the declaration against traces in the code and show you in the studio the points the code does not back up, before you click “Release”.

- **Art direction:** one visual direction: one palette, one style, scene and elements from one skin, no bare rectangles.
- **Animation:** every change of state has a transition, there is a win and a loss animation, and motion turns off for people who ask for that.
- **Sound:** a sound for every action and every result, mute in the settings, sound back after returning from the background.
- **Feedback on every move:** an answer to every action within 100 ms: picture, sound, vibration on a phone; it is clear whose move it is and why a move is not allowed.
- **Light and dark theme:** both variants following the device setting, plus a switch in the game.
- **Languages:** every text from a translation table, at least Polish and English, every declared language checked on a phone (not needed for a game with no words).
- **Online:** invite by link, waiting for the opponent, coming back after a disconnect, a rematch in one gesture (not needed for a solo game).

Leaderboard: a game that declares a score (`wynik_max`) but does not send it with `klyo.score` will not pass the gate as finished. A game with no points gives the reason in its description. The review can be skipped for a demo and a game in development, and for a plain fix (`zmiana: "poprawka"`) too.

## Common questions

### What does MCP mean here?

Model Context Protocol: the open standard that lets an AI assistant call tools on outside servers. It is not a hosting platform. klyo games is the platform, and MCP is the way your assistant talks to it: it uploads the package, fills in the description and brings back a playable link.

### Which AI assistants can publish a game on klyo?

Any client that supports remote MCP servers with sign-in. Step-by-step instructions are ready for Claude (claude.ai, the apps and Claude Code), ChatGPT in developer mode, Cursor, VS Code with Copilot, opencode and Gemini Enterprise. You add the server address once; the first tool call opens the klyo sign-in page and creates the account.

### Where does the assistant get the package address?

From wherever you already work: a repository, a drive, your own server. The address must be public and lead straight to a ZIP file with `index.html` at the top. A package may weigh up to 100 MB and hold up to 5,000 files.

### Does it work with Unity and Godot?

Yes, if you export for the browser. We accept WebAssembly files, Unity data and Godot packs the same as plain HTML with JavaScript.

### What if the game does not start?

You will see that in the preview, before you release anything. If the game is missing a file we say which one, and when moving a game from another portal we fetch the missing files from the source address.

### Can my assistant fix a game without a ZIP package?

Yes. `klyo_game_files` reads the game's files and `klyo_game_patch` edits the text files in a workshop, next to the version players have. You see the changes in the studio as “New version is waiting” and release them with one click. Images and sounds are still replaced with a package.

### Can the agent see what happens inside the game?

It sees what your own browser console would: the files the game asked for in vain, and the JavaScript errors in the order they happened. We collect them while the game is WAITING: in the package preview and at its own address before you press “Release to the catalogue”. The moment it is published we stop: the game then belongs to the player and sends us nothing.

### Does klyo pay for my AI or see my sign-in?

No. Your AI runs on your own subscription and your sign-in stays with you, just like in VS Code and Cursor. We only receive the finished text and publish nothing without your approval.

### How do I choose translation languages?

In the “Translate with your AI” window you press the languages you want. You can also say “now German” in the chat. Every language shows up in the “Translations” window for approval.

### How do I know my AI is connected to klyo?

The studio window tells you after the click: a ✓ and the name of the connected AI. The full list of connections and disconnecting live on the [connections page](https://panel.klyo.pl/mcp/connect).

### Why is my game page not in Google?

A game page enters Google when, in that language, it has at least 220 words of description written or accepted by the creator, plus a name and a tagline in that language. A shorter page carries a noindex, so a thin page does not drag the whole portal down. So does a page that repeats another game page by more than 42%: then add sentences that are only about this game. `klyo_my_games` shows the reason with numbers for every game in `tlumaczenia.indeks`, for example a description at 198 of the 220 words. Game pages exist in Polish and English, while texts can have ten languages.

### How do I check what Google sees right now?

`klyo_game_stats` with `sprawdz_google: true` asks Google about the game pages at that moment (once an hour per game) and gives, for each page, when we asked and when Google’s crawler last visited it. Re-indexing of an ordinary page is requested in Search Console with the button next to the address: Google does not accept that request through an API, and the sitemap already submits the page.

### When does a category page, like solitaire, appear?

When the category has at least three games. A page with one game is a copy of a tile to Google, and such pages pull the whole portal down. The first game in a category can rank high on its own through its game page with a full description; the category page joins at the third.

### My key does not see some tools. What now?

`klyo_status` lists the hidden tools, the reason (scope or account type) and how to unlock them. The `klyo:publish` scope covers preview edits (`klyo:edit_preview`), and new keys from the studio carry all scopes.

### The description check stopped my game. Why?

A refusal always names the word that caused it. The description is checked in the language of each tag (``, ``), and genre words, such as a shot in Battleships or shooting a bubble, do not require ticking violence in the survey. Violence means killing, blood, weapons and the shooter genre.

### How do I delete a package from the waiting room?

`klyo_delete_game` with `upload_id` instead of `slug`. A package that already became a game stays, because it is that game’s preview.

### The gate says “exceptions” but the game works. What does it mean?

An exception is a JavaScript error reported by the browser. Game state reports (`stan:`) and the recording log (`obraz:`, `kompozyt:`) are not exceptions and do not stop a release. A score sent through the kit held in a variable counts too: the preview then reports that the game sent a score.

### Do online games survive a dropped connection?

Yes. Every move has a number and its own id. When a phone loses the network for a moment, the page pulls the moves the player missed once it is back, once and in order, and a move sent at a bad moment retries by itself without being doubled. Quick match finds an opponent on its own, and “Leave room” really closes the room.

### A tool answer is too big for my assistant. What now?

Use `limit`. `klyo_ads_ideas` returns the most searched phrases (50 by default, with the total count), and with `tylko_zarodki` only the phrases you gave, with their numbers. `klyo_keyword_map` trims its lists to 40 and counts its summary from everything. `klyo_my_games` carries only the recording verdict for each game, without the measurements.

### Can I measure a game in chosen languages?

Yes. `klyo_game_diagnostics` with `zmierz`, `pelny` and `jezyki: ["pl","en","de"]` checks exactly those languages, together with the weak phone. A second measurement ordered while the first runs waits in the queue and starts by itself.

### Do I have to use an assistant?

No. Everything the tool does you can do in a browser at [dev.klyo.pl](https://dev.klyo.pl/): pick the package, see the game in a window straight away and fill in the description.

---

Source: https://games.klyo.pl/mcp/ · Built and run by klyo, a Polish technology company (Łódź) · Contact: kontakt@klyo.pl · Index for language models: https://games.klyo.pl/llms.txt
