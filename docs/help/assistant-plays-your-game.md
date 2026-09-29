> **Canonical page:** https://games.klyo.pl/support/assistant-plays-your-game/ · updated 2026-09-29 · This file is generated from the klyo games website, so changes are made on the website.

# Let your AI assistant play your game

Open the studio at dev.klyo.pl on the computer or phone you want to test on, and click “Allow” when your assistant asks to play. The game runs on your side, on your graphics card; your assistant sends moves and looks at screenshots. One click stops it.

## Before you start

- An AI assistant connected to klyo through the MCP server (Claude, ChatGPT or another).
- A game on your account: in the catalogue, in the workshop or in the waiting room.
- The game loads the klyo SDK from games.klyo.pl/sdk/klyo-gry-sdk.js.

## Step by step

1. **Ask your assistant to play**: Write in the chat, for example, “play my game and check level two”. Your assistant calls the play tool and tells you it is waiting for your permission.
2. **Open the studio**: Go to dev.klyo.pl on the computer or phone you want to test on. At the bottom of the screen you see “Your assistant wants to play …”.
3. **Click Allow**: Press **Allow**. From then on your assistant may play on this device, and the bar says “Your assistant may play on this device”. Go back to the chat and say it can start.
4. **Watch it play**: The game opens in a small window in the corner of the screen, full screen on a phone. You see every move, and your assistant gets screenshots and the game state. Keep the studio visible: browsers pause games in background tabs.
5. **Stop it or turn it off**: Press **Stop** in the game window or **Turn off** on the bar. The play ends at once, and your assistant's next request asks for your permission again.

## If something goes wrong

### I do not see my assistant's request

The request waits 10 minutes. Reload the studio or ask your assistant to try again. The studio has to be open on the same klyo account your assistant is connected to.

### My assistant says the studio is in the background

Browsers pause games in tabs you cannot see. Put the studio window next to the chat, or open the studio on your phone.

### My assistant says “no SDK”

The game does not load the klyo SDK, or carries an old copy in its package. Load it from games.klyo.pl/sdk/klyo-gry-sdk.js; your assistant can fix that in the workshop.

### There is no sound

Browsers turn sound on only after your own click in the game. Your assistant's moves cannot replace it, so click the game window once.

## Common questions

### Does the klyo server see my game?

It never displays it. The game runs on your device; the server only passes your assistant's moves and the screenshots to the chat that asked for them. We do not store the screenshots in a database or on disk.

### Can my assistant play someone else's game?

No. It opens only your account's games, the same version it reads and fixes in the workshop.

### Does it work with a 3D game?

Yes. The game uses your device's graphics card, so your assistant sees what you see. That is exactly the case where the measurement on our server says NIESPRAWDZONA.

## Related guides

- [Game shows a white screen: how to fix it](https://games.klyo.pl/support/white-screen/)
- [How to release a new version of your game or roll back](https://games.klyo.pl/support/release-new-version/)
- [All guides](https://games.klyo.pl/support/)

Still stuck? Write to [kontakt@klyo.pl](mailto:kontakt@klyo.pl) and include the address of the game. A person answers within two working days.

---

Source: https://games.klyo.pl/support/assistant-plays-your-game/ · Built and run by klyo, a Polish technology company (Łódź) · Contact: kontakt@klyo.pl · Index for language models: https://games.klyo.pl/llms.txt
