> **Canonical page:** https://games.klyo.pl/support/save-game-progress/ · updated 2026-11-10 · This file is generated from the klyo games website, so changes are made on the website.

# How to save player progress in an HTML5 game

Add the klyo SDK to index.html. Even without save code the game keeps progress: the SDK copies its localStorage and engine files to the cloud. To choose what progress is, call klyo.save.get at start and klyo.save.set after meaningful changes. Progress follows a signed in player to every device.

- 5 min read
- Steps: 5

### On this page

## Before you start

- A browser game (plain JavaScript, Godot, Unity, GameMaker or any engine that exports to the web) and access to its index.html.
- The game state as an object that fits in 64 KB, for example level, coins and settings.
- No server or database on your side: the SDK and the klyo page do the rest.

## Step by step

1. **Add the SDK**: Put this line in index.html before your own script: ``. An engine that exports to the web calls the same functions through its own way of calling JavaScript: in Godot that is `JavaScriptBridge`, in Unity a `.jslib` plugin.
2. **Load progress at start**: Call `klyo.save.get(callback)` once when the game starts. When `z.ok` is true and `z.data` is set, restore the game from `z.data`. `z.cloud` is true when the klyo server answered, and `z.reason` says why the data comes only from the browser.
3. **Save after meaningful changes**: Call `klyo.save.set(state, callback)` after a level, a purchase or a change of settings. The SDK keeps a copy in the browser and merges saves that come faster than every 2 seconds into one, so you do not need a timer of your own.
4. **Test it in the studio preview**: Upload the package and play in the preview window. Saves go to the preview cloud that only you can see, and the answer has `o.cloud` and `o.preview` set to true. Call `klyo.save.get` again, or open the preview again, and the same data comes back with `z.source` equal to "chmura".
5. **Publish the game**: After release every player saves into a slot of their own: a signed in player keeps progress on every device, a guest keeps it in this browser. Your preview save disappears together with the preview.

## If something goes wrong

### The answer says the data is local

`z.reason` tells you why. `bez-strony`: the game runs outside klyo (straight from a file or on another site), so progress stays in the browser. `bez-serwera`: there was no connection, and the SDK sends the copy again later. `pusto-w-chmurze`: the cloud had nothing yet, so the game got the browser copy and the SDK sent it to the cloud.

### My code waits and then gives up

The answer always arrives, at the latest after 8 seconds, and on klyo it arrives at once. Remove a shorter timeout of your own and start the game from the browser copy while the cloud answers.

### A save is rejected as too large

The answer has `reason` equal to `rozmiar`: the state is larger than 64 KB once encoded. Save only what you need to restore the game, not the whole scene.

### The preview quality gate says progress will not move to other devices

The klyo SDK is not the first script on the game page, so the copy of the game's storage arrives after the game has read it. Move the SDK line above every other script, or save progress with klyo.save.

## Does the player need an account to keep progress?

No. Without an account progress belongs to this browser. With an account it follows the player to every device, and the copy saved in this browser before signing in moves to the account.

## What happens when two devices save at the same time?

The latest save in the cloud wins. A browser copy that the server has not confirmed yet goes up only when no other device saved in the meantime, so an older copy never overwrites newer progress.

## Do players see my test saves from the preview?

No. The preview has a slot of its own that only you and klyo moderators can open, and it is deleted together with the preview.

## Is localStorage enough to save a browser game?

On klyo, yes. The SDK copies the game's localStorage to the cloud and writes it on the player's other device before the game starts, so progress moves from phone to computer without a line of code. Outside klyo a localStorage save stays in one browser and disappears when the player clears the site data.

## Do Godot and Unity saves work without any code?

Yes. The engine's save files (Godot, Unity and other engines with a web export) live in the browser's database, and the SDK copies them to the cloud and writes them on a new device before the engine reads them. The SDK must be the first script on the game page; when a package has no SDK, we add it there ourselves.

## What if the player has different progress on two devices?

The player chooses. A bar over the game says that this device has different progress than the account, with **Load from account** and **Keep this one**. Nothing is overwritten silently.

## How large can the game's storage be?

Up to 120 KB of localStorage and 120 KB of engine files per player and game. A single entry larger than 100 KB, such as an image or a cache, and the largest entries above that budget stay on the device only. Once saving through klyo.save works (the server confirmed a save), the SDK stops this copy: one save, one truth.

## Does the save survive a new version of the game?

Yes. The save belongs to the game's address and to the player's account, not to the files in the package, so a new version gets the same save. Before you release it, check this in the preview of the new version.

## How do I save progress from a Godot web export?

Through the engine's bridge to JavaScript: the game gets the klyo SDK object and a callback receives the answer. The SDK reference has a complete code example.

## How do I call the save from Unity WebGL?

From a JavaScript plugin in the project: a plugin function calls the klyo SDK, and the C# code declares that function and calls it like any other method.

## Related guides

- [SDK reference for saves, with a Godot example](https://games.klyo.pl/game-sdk/#zapis)
- [How to add a leaderboard to an HTML5 game](https://games.klyo.pl/support/add-leaderboard/)
- [How to publish an HTML5 game on klyo games](https://games.klyo.pl/support/publish-html5-game/)
- [How to release a new version of your game or roll back](https://games.klyo.pl/support/release-new-version/)
- [All guides](https://games.klyo.pl/support/)

Still stuck? Write to [kontakt@klyo.pl](mailto:kontakt@klyo.pl) and include the address of the game. A person answers within two working days.

---

Source: https://games.klyo.pl/support/save-game-progress/ · Built and run by klyo, a Polish technology company (Łódź) · Contact: kontakt@klyo.pl · Index for language models: https://games.klyo.pl/llms.txt
