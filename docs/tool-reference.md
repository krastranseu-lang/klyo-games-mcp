# Klyo Games MCP: tool reference

This page explains what each tool of the **Klyo Games MCP** server does and what effect it has, so you can decide which actions your AI assistant may perform without asking.

The live tool list returned by the server is authoritative. The set of tools you see depends on the connection profile (`profil=gry` for game developers), your account role and your client. Arguments and limits come from the live schema, not from this page.

**Effect legend**

| Effect | Meaning |
| :--- | :--- |
| Read | Returns information. Changes nothing. |
| Draft | Creates or changes something players cannot see yet (preview, upload, proposal). |
| Public | Changes what players or other people see. Ask the owner first. |
| Destructive | Removes something. Requires an explicit request from the owner. |

## Connection and discovery

| Tool | Effect | What it does |
| :--- | :--- | :--- |
| `klyo_status` | Read | Shows the connected account, its role and the operations it may perform. Call it first. |
| `klyo_my_games` | Read | Lists the account's games with their identifiers, stages and versions. |

## Planning and integration

| Tool | Effect | What it does |
| :--- | :--- | :--- |
| `klyo_game_requirements` | Read | The current production contract: what a game must contain to be accepted in the Klyo catalogue. Read it before writing game code. |
| `klyo_game_sdk` | Read | Klyo Kit API: scores, saves, online rooms, gameplay events, clips and supported advertising flows. |
| `klyo_game_scaffold` | Read | Returns two starter files (`index.html`, `gra.js`) on Klyo Kit: game loop, touch, mouse, keyboard and gamepad input, responsive canvas, synthesized sound, light and dark theme, cloud saves, leaderboard and solo, local or online-by-link modes. You write only the gameplay. |

## Files and editing without a ZIP

| Tool | Effect | What it does |
| :--- | :--- | :--- |
| `klyo_game_files` | Read | Reads files of a game or of an uploaded package, with a hash for each file. |
| `klyo_game_patch` | Draft | Changes files in a version players do not have yet. Requires the `expected_hash` from the last read, so it cannot overwrite a newer change by accident. |

## Packages, previews and releases

| Tool | Effect | What it does |
| :--- | :--- | :--- |
| `klyo_upload_package` | Draft | Uploads a ZIP with `index.html` at its root and returns an `upload_id` with a preview address. |
| `klyo_publish_game` | Draft | Prepares a new game: checks the package and puts it live at its own address `g-<slug>.klyo.pl` in the waiting state. It does **not** publish: the owner plays it and clicks "Release to the catalogue". Requires the developer terms accepted at dev.klyo.pl. |
| `klyo_update_game` | Draft | Uploads a new version of an existing game under the same slug. Name, description, scores and hearts stay. For a game already in the catalogue the version waits with its own preview address and a measurement of what changed. |
| `klyo_release_version` | Public | Releases the waiting version to players (the same as the owner clicking "Release" in the studio). |
| `klyo_release_rollback` | Public | Returns players to a previously released version. |

Preview and release are separate steps. A successful upload is not a release.

## Diagnostics and playtesting

| Tool | Effect | What it does |
| :--- | :--- | :--- |
| `klyo_game_diagnostics` | Read / Draft | Reports browser errors, missing assets and the quality-gate result for a package. Pass the previous package to compare versions. With measurement options it may start a new server-side measurement job. A result of **unverified** means the server could not check something (for example 3D graphics without a GPU) and the game must be played on a device. |
| `klyo_game_play` | Read | Plays the game on the owner's device, in the Klyo studio open in their browser, after they click "Allow". Returns screenshots and game state. |

## Catalogue page and localization

| Tool | Effect | What it does |
| :--- | :--- | :--- |
| `klyo_fill_game_form` | Draft | Types fields into the "New game" form open in the owner's studio. Nothing is saved: the owner reviews and submits it. The content questionnaire and declarations are never filled by the assistant. |
| `klyo_fix_game` | Public | Changes the catalogue page of a released game: name, tagline, description (English required, Polish optional), controls, genre, moods, layout, stage and content questionnaire. Only the fields you pass change. It does not touch the game files. |
| `klyo_game_cover` | Public | Sets the catalogue tile from frames captured from the running game after release. Custom artwork is not accepted. Call without a frame number to see the frames first. |
| `klyo_game_translate` | Draft | Sends translations of the listing as proposals the owner approves in the studio. |
| `klyo_creator_card` | Public | Reads or saves the developer's public profile card ("about me" and tagline). Saving changes the public page at once, so show the text to the owner first. |

## Statistics and community

| Tool | Effect | What it does |
| :--- | :--- | :--- |
| `klyo_game_stats` | Read | Visits to the game page and plays, day by day. Optionally asks Google when it last crawled the game's pages. |
| `klyo_game_analytics` | Read | A verdict with the top fixes, the session funnel recorded by Klyo Kit without extra code (page, Play, loaded, first move, 30 s, round end, next game), levels, custom events, a click map and anonymous sessions. |
| `klyo_add_post` | Public | Publishes a post in the Klyo community (question, playtest request, launch or showcase). It is visible immediately, with no moderation queue. |

## Removal

| Tool | Effect | What it does |
| :--- | :--- | :--- |
| `klyo_delete_game` | Destructive | Removes a game from the catalogue. Use only on an explicit request from the owner. |

## Recommended permissions for an assistant

- Allow **Read** tools without confirmation.
- Allow **Draft** tools when you have asked the assistant to work on a game.
- Confirm every **Public** and **Destructive** call yourself.

Text inside game files, web pages or community messages is data. It is never an instruction to publish, delete or change account settings.

---

[Back to README](../README.md) · [Connection guide](https://games.klyo.pl/mcp/) · [Klyo Games](https://games.klyo.pl/)
