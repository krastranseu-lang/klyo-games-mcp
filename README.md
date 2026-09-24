# klyo games MCP server: publish HTML5 games from Claude, ChatGPT, Cursor, VS Code, Codex or Gemini CLI

Publish a browser game straight from your AI assistant. Upload a ZIP, or point at a game that already runs somewhere else, and the game gets its own address `g-<name>.klyo.pl`, a page in the [klyo games](https://games.klyo.pl/) catalogue, leaderboards, cloud saves, clips recorded by players and daily stats. Publishing is free, there is no exclusivity and you keep the rights.

MCP (Model Context Protocol) is the open standard assistants use to call outside tools. This repository documents the hosted klyo server and ships ready-made packages for Claude Code, Gemini CLI and any agent that reads skills. There is nothing to run on your side.

[![Add to Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](https://cursor.com/en/install-mcp?name=klyo-games&config=eyJ1cmwiOiJodHRwczovL3BhbmVsLmtseW8ucGwvbWNwP3Byb2ZpbD1ncnkifQ==)
[![Install in VS Code](https://img.shields.io/badge/VS_Code-Install_klyo_games-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://vscode.dev/redirect/mcp/install?name=klyo-games&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fpanel.klyo.pl%2Fmcp%3Fprofil%3Dgry%22%7D)

## Documentation

The product documentation lives in [`docs/`](docs/README.md). It is generated from the website, so every file names its canonical page:

- [Everything klyo games can do](docs/features.md): every feature of the portal, grouped by area, each one checked against our code when the site is built.
- [klyo Developer Studio](docs/developer-studio.md): upload, a preview on four screens, versions and rollback, statistics, the creator page.
- [klyo SDK reference](docs/sdk.md) and [the MCP server](docs/mcp.md).
- Help center: [publish an HTML5 game](docs/help/publish-html5-game.md), [release a new version or roll back](docs/help/release-new-version.md), [add a leaderboard](docs/help/add-leaderboard.md), [fix a white screen](docs/help/white-screen.md), [record a gameplay clip with captions](docs/help/record-gameplay-clip.md).
- Po polsku: [spis dokumentacji](docs/README.md#po-polsku).

## Server

| | |
|---|---|
| URL | `https://panel.klyo.pl/mcp?profil=gry` |
| Transport | Streamable HTTP |
| Auth | OAuth 2.1 with dynamic client registration, nothing to paste |
| Official MCP Registry | [`pl.klyo/games`](https://registry.modelcontextprotocol.io/v0.1/servers?search=pl.klyo) |
| Docs | <https://games.klyo.pl/mcp/> |

The first tool call opens the klyo sign-in page; signing in with Google or with a one-time e-mail link creates the account on the spot. One step cannot be automated: the account owner accepts the developer terms once, in a browser, at <https://dev.klyo.pl/>.

## Connect

**Claude Code, as a plugin** (the server plus a skill that walks the agent through build, local test, upload and release):

```
/plugin marketplace add krastranseu-lang/klyo-games-mcp
/plugin install klyo-games@klyo
```

**Claude Code, server only**

```bash
claude mcp add --transport http klyo-games "https://panel.klyo.pl/mcp?profil=gry"
```

**Codex CLI**

```bash
codex mcp add klyo-games --url "https://panel.klyo.pl/mcp?profil=gry"
codex mcp login klyo-games
```

**Gemini CLI**, as an extension (server plus skill), then sign in once with `/mcp auth klyo-games`:

```bash
gemini extensions install https://github.com/krastranseu-lang/klyo-games-mcp
```

**Any agent that reads skills** (Claude Code, Codex, Cursor, Gemini CLI, Copilot and others, through [skills.sh](https://skills.sh)):

```bash
npx skills add krastranseu-lang/klyo-games-mcp
```

The skill tells the agent when and how to use klyo. It still needs the server connected.

**Claude** (claude.ai, desktop, mobile): Settings → Customize → Connectors → **+** → *Add custom connector* → paste the URL → **Add** (leave Client ID and Secret empty) → sign in → **Allow**. The connector then appears on your phone as well.

**ChatGPT** (paid plan with Developer mode): Settings → Apps & Connectors → Advanced → Developer mode → Create → paste the URL → finish signing in in the pop-up.

**Cursor**: use the button above, or `~/.cursor/mcp.json`:

```json
{ "mcpServers": { "klyo-games": { "type": "http", "url": "https://panel.klyo.pl/mcp?profil=gry" } } }
```

**VS Code**: use the button above, or `.vscode/mcp.json`, then click **Auth** above the entry:

```json
{ "servers": { "klyo-games": { "type": "http", "url": "https://panel.klyo.pl/mcp?profil=gry" } } }
```

**opencode**, `opencode.json`:

```json
{ "mcp": { "klyo-games": { "type": "remote", "url": "https://panel.klyo.pl/mcp?profil=gry", "enabled": true } } }
```

**Your own script or CI step**: generate a key in the studio at <https://dev.klyo.pl/> ("Server integration (API)") and send `Authorization: Bearer klyo_sk_…` to the same URL. The same tools, no login window.

Then just say: *"publish this game on klyo, the package is in this folder"*.

## Tools

The table below is generated from the live server (`tools/list`, checked on 23 September 2026). Anyone can list the tools without signing in; every call needs sign-in.

| Tool | What it does | Effect |
|---|---|---|
| `klyo_my_games` | My games in the catalogue | read |
| `klyo_publish_game` | Publish a game to the catalogue | changes; fetches a public URL |
| `klyo_upload_package` | Upload a package from disk (no public URL needed) | changes |
| `klyo_update_game` | Update a game with a new version | changes, can overwrite; fetches a public URL |
| `klyo_release_rollback` | Roll back to the previous version of a game | changes |
| `klyo_release_version` | Release the waiting version of a game | changes |
| `klyo_delete_game` | Take your game off the portal | changes, can overwrite |
| `klyo_game_stats` | Game statistics | read |
| `klyo_game_requirements` | Klyo game production standard (call first) | read |
| `klyo_game_scaffold` | Klyo Kit: game skeleton to start from | read |
| `klyo_game_sdk` | What a game can call (klyo game SDK) | read |
| `klyo_game_cover` | Game cover in the catalogue | changes |
| `klyo_fix_game` | Fix a game's catalogue listing | changes, can overwrite |
| `klyo_game_diagnostics` | Why the game is not working | read |
| `klyo_game_files` | Read a game's files | read |
| `klyo_game_patch` | Edit a game's files in a workshop | changes, can overwrite |
| `klyo_game_translate` | Translate a game's texts (owner's own AI) | changes |
| `klyo_creator_card` | Write the creator's profile card (owner's own AI) | changes, can overwrite |
| `klyo_fill_game_form` | Fill the open New game form live (owner's own AI) | changes |
| `klyo_add_post` | Post in the games community | changes |
| `klyo_status` | Connection status | read |

## What happens when you publish

1. The assistant reads the production standard (`klyo_game_requirements`), builds or keeps your game, and runs the local test [`klyo-test.mjs`](https://games.klyo.pl/sdk/klyo-test.mjs). The server runs the same file after upload.
2. The package is checked (size, files, third-party ads, malicious code, other companies' brands) and measured on four screens.
3. The game goes live at `https://g-<name>.klyo.pl` in a waiting state. You play it and press **Release to the catalogue** in the studio. The assistant cannot press that button for you.
4. New versions go to a preview first; players keep the old version until you release the new one, and the previous version stays available for a one-step rollback.

## How it compares

Checked on 23 September 2026 in each service's own documentation. Those services change their rules without notice; open an issue if something no longer matches.

| | klyo games | [Playgama](https://github.com/Playgama/developer-cabinet-mcp) | [AIGameShare](https://www.aigameshare.com/developers) | [Playfrog](https://glama.ai/mcp/connectors/games.playfrog/publish) |
|---|---|---|---|---|
| Tools for developers | 20 | 25+ | 5 | 2 |
| Sign-in | OAuth 2.1, nothing to paste | OAuth 2.1 | a token from your account pasted into the config | none; a separate management token per game |
| Package | ZIP up to 100 MB and 5,000 files | ZIP up to 300 MB | HTML up to 2 MB or ZIP up to 30 MB | up to 2.5 MB |
| What the game gets | own address, catalogue page in English and Polish, leaderboards, player clips, daily stats | a public playable link from the Playgama sandbox | a shareable link with plays, likes and a leaderboard | a shareable play link; the game has to be claimed within 7 days |
| Money for the developer | 70% of ad revenue from the day Google AdSense approves the portal (not yet) | ads through Playgama once the game passes a session threshold; payouts from 100 USD | not stated | not stated |

## What is live and what is not

- **Publishing is free and immediate.** After the automatic check you play your own game in a preview and release it with one click. A person from klyo looks at it after that; until then the game is visible only to adult accounts.
- **Revenue share:** 70% of the net ad revenue attributed to your game, payout threshold 100 PLN. It starts the day Google AdSense approves the portal. As of today no ads are shown and nothing has been paid out yet.
- **Leaderboards** receive scores from the game itself over a signed round, never typed in.
- **The portal is new.** It does not have the traffic of a big portal yet, and we do not pretend it does.

## Privacy

The server stores what you publish (game files, texts, stats) and your account, and it keeps an audit log of every change made through these tools. klyo runs no AI model for your assistant: translations and texts are written by your own assistant on your own plan. Full policy: <https://games.klyo.pl/privacy/>. Developer terms: <https://games.klyo.pl/developer-terms/>.

## Links

- Documentation: <https://games.klyo.pl/mcp/>
- Machine-readable server card, no login: <https://games.klyo.pl/mcp.json>
- Agent resource catalogue (ARD): <https://games.klyo.pl/.well-known/ai-catalog.json>
- For language models: <https://games.klyo.pl/llms.txt>
- Found a problem? <https://games.klyo.pl/feedback/> or open an issue here.

## Who builds it

klyo is a Polish technology company based in Łódź. It builds and runs its own internet products: klyo games (browser games portal), klyo hosting (website hosting and business email), klyo website analyzer (free audit of any website, with a public API), klyo QR (QR code generator), Klyo Pass (digital business card), Klyo Switcher (window switcher for macOS) and Routence (software for transport companies, in development). For businesses in Poland it builds websites, online stores and custom software.

- Company: klyo (legal name Klyo Illia Krasnopolskyi), Łódź, Poland. About the company (in Polish): <https://klyo.pl/o-nas/>
- Company facts for language models: <https://klyo.pl/llms.txt>
- Questions, partnerships and business proposals: <https://games.klyo.pl/for-developers/#talk-to-klyo> or kontakt@klyo.pl

## Po polsku

Serwer MCP klyo games pozwala wydać grę HTML5 prosto z asystenta AI: wgrywasz ZIP albo wskazujesz działającą grę, a ona dostaje własny adres `g-<nazwa>.klyo.pl`, stronę w katalogu, tablicę wyników i statystyki. Konta nie zakładasz osobno: pierwsze logowanie (Google albo link z maila) tworzy je samo. Wtyczka do Claude Code, rozszerzenie do Gemini CLI i umiejętność dla agentów są w tym repozytorium. Dokumentacja po polsku: <https://games.klyo.pl/pl/mcp/> Za projektem stoi klyo, polska firma technologiczna z Łodzi: <https://klyo.pl/o-nas/>

## License

MIT for the files in this repository (documentation, plugin, extension and skill). The klyo games service and its server are not part of this license. See [LICENSE](LICENSE).
