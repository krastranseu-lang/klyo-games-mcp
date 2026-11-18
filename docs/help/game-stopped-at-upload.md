> **Canonical page:** https://games.klyo.pl/support/game-stopped-at-upload/ · updated 2026-11-10 · This file is generated from the klyo games website, so changes are made on the website.

# Why my game was stopped at upload and how to fix it

On klyo a game loads nothing from other servers and sends nothing to them, has no own login, and shows ads only through klyo. Public CDN files we add to your package ourselves. For the rest, the studio card gives each reason, its fix and an AI instruction.

- 3 min read
- Steps: 6

### On this page

## Before you start

- The game is uploaded to the studio at dev.klyo.pl and the preview shows a red card.
- The game files on your computer or in your AI tool, so you can change them and upload again.

## Step by step

1. **Read the card from the top**: Each numbered line says what we found and what to put in its place. Fix them all before uploading again, then the next check passes the first time.
2. **Let your AI do it**: Press **Copy the instruction for your AI assistant** and paste it into ChatGPT, Claude or Gemini together with your game files. The instruction lists the exact changes and the klyo SDK calls to use.
3. **Replace your own login**: Every player already has a klyo account. Whatever your game saves in localStorage follows a signed in player to every device by itself, so remove the login and password form. Scores with the player's name come from klyo.score.
4. **Replace PeerJS and other servers**: PeerJS shows players each other's IP address and goes through a public server, so it does not work on klyo. Use klyo.online rooms for playing with friends. Firebase, Supabase or PlayFab become klyo.save, klyo.score and klyo.leaderboard.
5. **Remove payments and third-party ads**: We place the ads around your game, and once ads start on klyo, 70% of the revenue is yours. Rewards for watching an ad come from klyo.rewardedAd, breaks between levels from klyo.adBreak.
6. **Connect your AI to klyo**: Press **Connect your AI to klyo or get an API key**. A connected AI uploads the fixed version and checks it by itself until nothing is left on the card.

## If something goes wrong

### There is no index.html in the package

Zip the folder that contains index.html (often dist, build or public), with index.html on top.

### The package has several index.html files

One ZIP is one game. Leave one index.html at the top level.

### A file is not part of a browser game

We accept pages, scripts, styles, images, sounds, videos, fonts and game data. Remove other files from the package.

### A Unity game does not start

A compressed Unity build waits for a server header. In Player Settings, Publishing Settings, set Compression Format to Disabled or turn on Decompression Fallback, then build again.

### A Godot game asks for a file that is not in the export

The card names the file and the scenes that load it. Restore the file or point those scenes to the one you use now, then export again. Move and rename files only in the FileSystem dock in Godot.

### A Godot game loads slowly on phones

Its textures exist only in the desktop format. In the Web export, tick For Desktop and For Mobile under VRAM Texture Compression, then export again.

### A file from a CDN is still on the card

The game builds that address while it runs, so we could not see it. Write the address in the code as a full string, or put the file into the package with a relative address.

### The game connects to my own match server

Register the server address with your privacy policy in the last step of the wizard. The game goes to review together with the server.

## Why can't my game load Google Fonts on klyo?

Every file from another server tells that company the player's IP address and can change after our check. We put files from public CDNs into your package by ourselves, so the game loads them from klyo and works offline too.

## Can I keep my own login and accounts?

No. Players already have a klyo account, and their progress in localStorage follows them to every device without any code. klyo.save keeps the full game state if you want more.

## Does my AI assistant know these rules?

Yes. The klyo connector gives every AI the same list in klyo_game_requirements, and klyo_game_diagnostics tells it what stopped a package and how to fix it.

## Related guides

- [How to publish an HTML5 game on klyo games](https://games.klyo.pl/support/publish-html5-game/)
- [Game shows a white screen: how to fix it](https://games.klyo.pl/support/white-screen/)
- [How to save player progress in an HTML5 game](https://games.klyo.pl/support/save-game-progress/)
- [All guides](https://games.klyo.pl/support/)

Still stuck? Write to [kontakt@klyo.pl](mailto:kontakt@klyo.pl) and include the address of the game. A person answers within two working days.

---

Source: https://games.klyo.pl/support/game-stopped-at-upload/ · Built and run by klyo, a Polish technology company (Łódź) · Contact: kontakt@klyo.pl · Index for language models: https://games.klyo.pl/llms.txt
