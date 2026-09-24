> **Canonical page:** https://games.klyo.pl/support/white-screen/ · updated 2026-09-24 · This file is generated from the klyo games website, so changes are made on the website.

# Game shows a white screen: how to fix it

Press “Show what happened” in the studio preview. It lists the files the game asked for and did not get, and the errors it threw. Most white screens come from capital letters in file names, absolute paths or scripts loaded from another server.

## Before you start

- The game is uploaded to the studio at dev.klyo.pl; a package still waiting for a description is enough.
- The original files on your computer, so you can fix them and upload again.

## Step by step

1. **Open the diagnosis**: In the preview press **Show what happened**. You see missing files and browser errors in the order they happened, the same list your AI assistant gets from the diagnostics tool.
2. **Check file names letter by letter**: Our server tells capital letters apart: Player.png and player.png are two different files. A game that works on Windows or macOS can miss files here, so make the names in the code match the files exactly.
3. **Use relative paths**: Load files as assets/hero.png, not /assets/hero.png, C:\ or file:///. Keep index.html in the root of the ZIP, not inside a subfolder.
4. **Keep every file inside the package**: A game on klyo loads its own files. A library, font or script from another server may not load, and code that sends data outside klyo does not pass the check. Put the file into the ZIP.
5. **Export engine games as a ZIP**: GameMaker, Unity and Godot build some file names while the game runs, so moving such a game from an address can miss them. Export the game to a ZIP in your engine and upload the whole folder.
6. **Test before you upload again**: On your computer run `node klyo-test.mjs http://localhost:8080/ my-game ./klyo-test`. It measures the game the way we do at release, with the same limits, and shows what a player would see.

## If something goes wrong

### The screen stays empty for a long time

The first frame should appear within 20 seconds, and the first download should stay under 20 MB on phones. Load large files later, after the menu is on screen.

### There is no sound

Browsers start sound only after the first tap or click. Resume the audio in a player gesture, also after the game comes back from the background on an iPhone.

### Nothing in the list explains it

Press **Talk to us** in the studio and send the game address with a screenshot. A person reads it.

## Common questions

### Why does the game work on my computer but not on klyo?

Usually because of capital letters in file names, absolute paths or files loaded from another server. A local computer forgives these; a web server does not.

### Can my AI assistant find the cause?

Yes. Connected over the klyo MCP server, it reads the same diagnosis, missing files and browser errors, and can patch the files in a draft version for you to play and release.

## Related guides

- [How to publish an HTML5 game on klyo games](https://games.klyo.pl/support/publish-html5-game/)
- [How to release a new version of your game or roll back](https://games.klyo.pl/support/release-new-version/)
- [How to add a leaderboard to an HTML5 game](https://games.klyo.pl/support/add-leaderboard/)
- [All guides](https://games.klyo.pl/support/)

Still stuck? Write to [kontakt@klyo.pl](mailto:kontakt@klyo.pl) and include the address of the game. A person answers within two working days.

---

Source: https://games.klyo.pl/support/white-screen/ · Built and run by klyo, a Polish technology company (Łódź) · Contact: kontakt@klyo.pl · Index for language models: https://games.klyo.pl/llms.txt
