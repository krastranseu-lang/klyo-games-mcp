# klyo games — MCP server for publishing HTML5 browser games

Publish and manage an HTML5 browser game straight from your AI assistant — Claude, ChatGPT, Cursor, VS Code, opencode or any MCP client. Upload a ZIP or point at a game that already runs somewhere else; the game gets its own address `g-<name>.klyo.pl`, live stats and a place in the [klyo games](https://games.klyo.pl/) catalogue. You keep the rights, with no exclusivity.

This repository documents the hosted server. There is nothing to install or run.

## Server

| | |
|---|---|
| URL (games) | `https://panel.klyo.pl/mcp?profil=gry` |
| URL (full klyo server: games, websites, hosting) | `https://panel.klyo.pl/mcp` |
| Transport | Streamable HTTP |
| Auth | OAuth 2.1 with dynamic client registration — no API key to paste |
| Official MCP Registry | `pl.klyo/games` |

## Account

There is no separate sign-up. The first time your assistant connects, it opens the klyo login page; signing in with Google or with a one-time email link creates the account on the spot. Publishing needs one step that cannot be automated: accepting the developer terms once, in a browser.

## Connect

**Claude** (claude.ai, desktop, mobile) — Settings → Customize → Connectors → **+** → *Add custom connector* → paste the URL → **Add** (leave Client ID and Secret empty) → sign in → **Allow**. The connector then appears on your phone as well.

**Claude Code**

```bash
claude mcp add --transport http klyo "https://panel.klyo.pl/mcp?profil=gry"
```

**ChatGPT** — needs a paid plan (Plus, Pro, Team, Business, Enterprise or Edu) and Developer mode: Settings → Apps & Connectors → Advanced → Developer mode → Create → paste the URL → finish signing in in the pop-up.

**Cursor** — `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "klyo": { "type": "http", "url": "https://panel.klyo.pl/mcp?profil=gry" }
  }
}
```

**VS Code** — `.vscode/mcp.json` (then click **Auth** above the server entry):

```json
{
  "servers": {
    "klyo": { "type": "http", "url": "https://panel.klyo.pl/mcp?profil=gry" }
  }
}
```

**opencode** — `opencode.json`:

```json
{
  "mcp": {
    "klyo": { "type": "remote", "url": "https://panel.klyo.pl/mcp?profil=gry", "enabled": true }
  }
}
```

Each of these clients opens the sign-in page itself the first time a klyo tool is used — there is no key to put in the file.

Then just say: *"publish this game on klyo, the package is in this folder"*.

## Tools

The list below is taken from the live server (`tools/list`), not written by hand. Every tool requires signing in; without a token the server returns `401`.

| Tool | What it does | Effect |
|---|---|---|
| `klyo_my_games` | My games in the catalogue | read |
| `klyo_publish_game` | Publish a game to the catalogue | changes |
| `klyo_upload_package` | Upload a package from disk (no public URL needed) | changes |
| `klyo_update_game` | Update a game with a new version | changes |
| `klyo_release_rollback` | Roll back to the previous version of a game | changes |
| `klyo_release_version` | Release the waiting version of a game | changes |
| `klyo_delete_game` | Delete your game | changes (destructive) |
| `klyo_game_stats` | Game statistics | read |
| `klyo_game_requirements` | Klyo game production standard (call first) | read |
| `klyo_game_scaffold` | Klyo Kit — game skeleton to start from | read |
| `klyo_game_sdk` | What a game can call (klyo game SDK) | read |
| `klyo_game_cover` | Game cover in the catalogue | changes |
| `klyo_fix_game` | Fix a game's catalogue listing | changes |
| `klyo_game_diagnostics` | Why the game is not working | read |
| `klyo_add_post` | Post in the games community | changes |
| `klyo_status` | Connection status | read |

## What is live and what is not

- **Publishing is free and immediate.** After the automatic check you play your own game in a preview and release it to the catalogue with one click. A person from klyo looks at it after that.
- **Revenue share:** 70% of the net ad revenue attributed to your game, payout threshold 100 PLN. It starts the day Google AdSense approves the portal — as of today no ads are shown and nothing has been paid out yet.
- **Leaderboards** receive scores from the game itself over a signed round, never typed in. A score made offline waits on the device and arrives when the connection returns.

## Links

- Documentation: <https://games.klyo.pl/mcp/>
- Machine-readable server card, no login: <https://games.klyo.pl/mcp.json>
- Agent resource catalogue (ARD): <https://games.klyo.pl/.well-known/ai-catalog.json>
- For language models: <https://games.klyo.pl/llms.txt>
- Found a problem? <https://games.klyo.pl/feedback/>

## Po polsku

Serwer MCP klyo games pozwala wydać grę HTML5 prosto z asystenta AI: wgrywasz ZIP albo wskazujesz działającą grę, a ona dostaje własny adres `g-<nazwa>.klyo.pl`, statystyki na żywo i miejsce w katalogu. Konta nie zakładasz osobno — pierwsze logowanie (Google albo link z maila) tworzy je samo. Dokumentacja po polsku: <https://games.klyo.pl/pl/mcp/>
