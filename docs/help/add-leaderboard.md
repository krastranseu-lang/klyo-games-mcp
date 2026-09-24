> **Canonical page:** https://games.klyo.pl/support/add-leaderboard/ · updated 2026-09-24 · This file is generated from the klyo games website, so changes are made on the website.

# How to add a leaderboard to an HTML5 game

Add the klyo SDK script to index.html, call klyo.ready() when the game can be played, klyo.progress() during a round and klyo.score() at the end. Set the highest possible score in the studio, and the game gets daily, weekly and all-time boards.

## Before you start

- A game published on klyo games, or ready to be uploaded.
- Access to the game's index.html. No server, database or accounts are needed on your side.
- Or an AI assistant connected over MCP: tell it to add the klyo leaderboard to the game.

## Step by step

1. **Add the SDK**: Put this line in index.html before your own script: ``. Opened outside klyo, the game keeps working and scores simply stay in the browser.
2. **Tell the page the game is ready**: Call `klyo.ready()` once the game has loaded and can be played. The page then hides the loading cover.
3. **Report progress during a round**: Call `klyo.progress(points)` whenever the score changes. The SDK sends at most four updates a second, and the page shows the player a goal under the game, such as #14 and the points needed to pass the next player.
4. **Send the final score**: At the end of a round call `klyo.score(points, callback)`. The answer carries today's position, this week's and all time, plus the player just above, ready for your end screen. One best score per device per day counts.
5. **Set the score cap**: In the studio, fill in the field “Highest possible score in one round” when you describe the game. Scores above it are rejected at once, and the game's tile on the records hub gets a cap mark. Without a cap, a score ten times higher than the next one waits for review.
6. **Show the board inside the game (optional)**: `klyo.leaderboard.get("day", callback)` returns the 20 best scores for day, week or all time, with the same player names the community shows.

## If something goes wrong

### Scores do not appear

A score counts only after a round of at least 3 seconds and only when the game runs on klyo. Check that the SDK loads before your own script and that klyo.ready() is called.

### A score is rejected

It is above the cap you set, or it came too soon after the previous score from the same device.

### Players ask where the board is

It stands on the game page and on the records hub by itself. Inside the game you draw it only if you call klyo.leaderboard.get.

## Common questions

### Do players need an account for the leaderboard?

No. A score belongs to the device; with an account the player's name goes on the board and the score follows them to their other devices.

### Can players cheat the leaderboard from the browser console?

No. A score is accepted only with a token the server signs when the round starts, after at least 3 seconds of play and below the cap you set, so typing a number into the console does not work.

## Related guides

- [How to publish an HTML5 game on klyo games](https://games.klyo.pl/support/publish-html5-game/)
- [How to release a new version of your game or roll back](https://games.klyo.pl/support/release-new-version/)
- [Game shows a white screen: how to fix it](https://games.klyo.pl/support/white-screen/)
- [All guides](https://games.klyo.pl/support/)

Still stuck? Write to [kontakt@klyo.pl](mailto:kontakt@klyo.pl) and include the address of the game. A person answers within two working days.

---

Source: https://games.klyo.pl/support/add-leaderboard/ · Built and run by klyo (Łódź, Poland) · Contact: kontakt@klyo.pl · Index for language models: https://games.klyo.pl/llms.txt
