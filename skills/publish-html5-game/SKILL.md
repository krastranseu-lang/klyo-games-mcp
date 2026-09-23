---
name: publish-html5-game
description: Publish, host or update an HTML5 browser game on klyo games (games.klyo.pl) through the klyo MCP server. Use when the user wants to put a web game online, get a playable link to share, publish a game made with AI or with Phaser, Three.js, PixiJS, Godot (web export), Unity WebGL or plain JavaScript, add leaderboards or cloud saves, release a new version, roll back, or find out why a published game shows a blank screen.
---

# Publish an HTML5 game on klyo games

klyo games is a catalogue of browser games with open self-publishing. A game gets its own address `https://g-<slug>.klyo.pl`, a catalogue page in English and Polish, leaderboards, cloud saves, clips recorded by players and daily stats. Publishing is free, there is no exclusivity and the developer keeps the rights.

## 1. Check the connection

The tools below come from the hosted MCP server `https://panel.klyo.pl/mcp?profil=gry` (streamable HTTP, OAuth 2.1). If no `klyo_*` tools are available, tell the user how to add it and stop:

- Claude Code: `claude mcp add --transport http klyo-games "https://panel.klyo.pl/mcp?profil=gry"`
- Codex CLI: `codex mcp add klyo-games --url "https://panel.klyo.pl/mcp?profil=gry"`, then `codex mcp login klyo-games`
- Gemini CLI: `gemini extensions install https://github.com/krastranseu-lang/klyo-games-mcp`, then `/mcp auth klyo-games` inside Gemini CLI
- Claude, ChatGPT, Cursor, VS Code and others: https://github.com/krastranseu-lang/klyo-games-mcp#connect

The first tool call opens the klyo sign-in page (Google or a one-time e-mail link) and creates the account. Once per account the owner accepts the developer terms in a browser at https://dev.klyo.pl/. You cannot do that step for them.

Call `klyo_status` first: it reports the account role and whether writing is allowed.

## 2. Read the production standard before touching code

Call `klyo_game_requirements` before you design, write or change game code. It returns the current standard (screens, touch and keyboard input, sound, leaderboard, quality gate, release steps). Follow it instead of asking the user about phone support, sound or leaderboards: the answers are in the standard.

- New game: `klyo_game_scaffold` returns a Klyo Kit skeleton (menu, pause, game over, settings, input, leaderboard, online rooms). You write only the gameplay.
- Existing game in any engine: keep the engine. The server adds the klyo SDK script to `index.html` by itself. Call `klyo_game_sdk` for the calls the game should make (ready, score, save, rewarded ads, clips).

## 3. Test locally, then package

1. Download the local test: https://games.klyo.pl/sdk/klyo-test.mjs (Node 22 or newer, Chrome or Chromium).
2. Serve the game folder, for example `npx serve . -l 8080`.
3. Run `node klyo-test.mjs http://localhost:8080/ <slug> ./klyo-test --uklad=pion` (`pion` = portrait, `poziom` = landscape, `oba` = both; use the layout you will declare when publishing).
4. Fix and repeat until there are no critical errors. The server runs the same file with the same thresholds after upload.
5. Package a ZIP with `index.html` at the root and only relative paths. Limit: 100 MB.

## 4. Upload and publish

1. `klyo_upload_package` returns a one-hour upload ticket and the exact two HTTP requests to send the ZIP (curl works). Do not save the ticket in project files. A game already hosted as a public ZIP can skip this step: pass `zip_url` instead.
2. `klyo_game_diagnostics` with the `upload_id` builds a preview (`adres_podgladu`), measures it on four screens and returns the quality gate (`bramka`). The measurement takes up to two minutes: call again until `pomiar_ekranow` is true. If you have a browser, open the preview and play it, so errors from your run land in the report too. Fix, upload again, repeat until the gate has no critical items.
3. `klyo_publish_game` with `etap` (`w_budowie` = in development, `demo`, `gotowa` = finished), the name, tagline, a player-facing description in English (at least 25 words; Polish is optional), genre, text language and the content questionnaire.
4. The game now runs at `https://g-<slug>.klyo.pl` and waits. Tell the user to open it, play it and click "Release to the catalogue" in the studio at https://dev.klyo.pl/. Do not say the game is published before the owner has done that.
5. Afterwards: `klyo_game_translate` (you translate the texts into the other klyo languages; the owner approves them in the studio), `klyo_game_cover`, `klyo_game_stats`.

## 5. Update, fix, roll back

- New build: `klyo_update_game` with the same `slug`. It goes to a preview; after the owner has played it, call `klyo_release_version`. Never create a second game to ship a fix, it splits players and scores between two addresses.
- Small change without a ZIP: `klyo_game_files` to read, `klyo_game_patch` to edit a workshop copy. Players keep the current version until you release the new one.
- A release broke the game: `klyo_release_rollback`.
- Blank screen or errors: `klyo_game_diagnostics` with the `slug`.
- Numbers: `klyo_game_stats`.

## Rules the server enforces

- Texts for players (name, tagline, description, release notes, posts) must not use a long dash (— or –) as a separator. Use a comma, a colon or a full stop. The server rejects such text.
- Ads only through `klyo.adBreak()` and `klyo.rewardedAd()` from the klyo SDK. A package with another ad network is rejected.
- Original games only: no other companies' brands, names or assets.
- The content questionnaire and age answers are statements of fact, and the developer terms are the owner's decision. Never invent them.

## What the developer gets, as of 2026-09-23

- Free publishing, own address, catalogue page, leaderboards with signed scores, cloud saves, player clips, stats.
- 70% of the net ad revenue attributed to the game, from the day Google AdSense approves the portal. Approval is still pending, so no ads are shown and nothing has been paid out yet. Payout threshold: 100 PLN.
- Docs: https://games.klyo.pl/mcp/ · Developer terms: https://games.klyo.pl/developer-terms/ · Privacy: https://games.klyo.pl/privacy/ · Problems: https://games.klyo.pl/feedback/
