> **Canonical page:** https://games.klyo.pl/playtesting/ · updated 2026-11-18 · This file is generated from the klyo games website, so changes are made on the website.

# Playtesting *with a recording* of every tester's game

Post a link to your game wherever you talk about it. Anyone who agrees to the test leaves you a recording with the game picture, cursor, taps and keys. In the studio you see where they got lost and what they tapped in vain.

[Open the developer studio](https://dev.klyo.pl/)

[AI assistants and MCP](https://games.klyo.pl/mcp/)

The animation is a real FRONTBREAK test from 18 November 2026, recorded on an ordinary computer from a developer's link.

dev.klyo.pl · Results · Tester recordings

![The playtest player in the klyo studio: video of the FRONTBREAK game, the tester's cursor and a timeline of their taps](https://games.klyo.pl/foto/testy-gier-film-en-1280.b39111c6.jpg)

*The player in the studio: video of a 3D game (WebGPU), the tester's cursor and a timeline of their taps. Long idle moments skip by themselves.*

## Three steps to your first recording

A link takes a minute, and you can watch the recording before the tester stops playing.

1. **Name a link**: In the studio, under the game's Results, you create a link, give it a name such as “Reddit” and pick the page language. Visits, people and tests count per link, without your own visits.
2. **The tester decides**: Before the game starts, the tester sees a card with what we record and what we do not. Without consent the game simply starts as usual. Tests are for people aged 16 and over.
3. **You watch right away**: The recording appears in the studio without reloading the page, with a frame of the game as its cover, the date and the time. When someone is playing right now, a “live” mark lights up next to it.

## Video of the game, WebGL and WebGPU included

Most browser games draw on a canvas. Session recording tools replay the page's code rather than its picture, so the canvas stays empty in them. Microsoft Clarity says so plainly in its frequently asked questions.

Our recorder takes a picture of the canvas right after the game draws a frame, even when the engine (Three.js, Unity, Godot and others) draws outside the usual animation loop. The browser's video encoder scales it to 640 pixels and 10 frames per second. Dialogs and buttons that the game puts in HTML above the canvas are added separately, so menus and labels show up in the recording too.

Every video frame carries game time. Cursor, fingers and keys line up with the picture frame by frame, and you scrub the timeline like any video.

- **640 px at 10 frames per second**: Enough to follow the movement and read the labels. A minute of play weighs about 2 MB.
- **The game does not slow down**: In our test the game drew 1,086 frames with the video and 1,107 without it in the same time.
- **2D and 3D games**: 2D canvas, WebGL and WebGPU. A game without a canvas replays from the recorded moves, without video.
- **48 hours**: After that the video and the log delete themselves. All videos together have a hard storage limit on our server.

[Source: Microsoft Clarity, frequently asked questions, as of 18 November 2026.](https://learn.microsoft.com/en-us/clarity/faq)

## Where the game does not respond

We took three signals known from website analytics and brought them to the game canvas.

![Close-up of the player: two dead taps on the FRONTBREAK minimap marked “nothing happened”](https://games.klyo.pl/foto/testy-gier-martwe-en-720.402cb037.jpg)

*The tester taps the FRONTBREAK minimap twice and nothing happens. The player marks both taps as dead.*

- **Dead tap**: A tap after which nothing changed for a second, neither in the game picture nor on the page. We compare it with the second before the tap, so an animated background raises no false alarm.
- **Rage clicks**: At least three quick taps on one spot, two of them dead. It usually means the button is too small, covered, or the game is waiting without any sign.
- **Idle skipping**: When the tester does nothing and the picture stands still, the player jumps ahead and says how much it skipped. When the picture moves, that part plays four times faster.

## A fix list for your AI assistant

We turn the recordings into a report. Dead taps carry the name of the element under the finger and its place on the screen in percent, JavaScript errors carry their exact text, and when a tester leaves the game we save the labels that were on their screen at that moment.

An assistant connected through MCP (Claude, ChatGPT, Cursor and others) reads this report in the klyo_game_analytics tool as its first tasks. It has evidence from the recording, so it fixes the game with klyo_game_files and klyo_game_patch, and you check the fix with a new test from the same link.

This is the report after the FRONTBREAK test in which the tester tapped the minimap:

`Game frontbreak: what to fix according to 5 recordings of real testers from the last 48 h.
• Dead taps on the game canvas, 11% from the left and 19% from the top of the screen: 2 in 1 of 5 recordings
Why: Players tap here and nothing changes for a second: they expect a button, a choice or a way forward.
What to do: Watch the moment from the evidence and see what the player is looking for.
Evidence (studio → Results → Tester recordings): Tester 6, 0:59`

## What the developer sees, and what they do not

A test is about the game, not about the person. These rules apply to every recording.

- **Consent first**: Nothing is recorded until the tester agrees on the card shown before the game. They can stop the recording at any moment with the button on the game.
- **A pseudonym, not a nickname**: The developer sees a numbered tester, the country and the device type. They never see the tester's account or nickname.
- **Only the game**: We record the game itself. The rest of the screen, the camera, the microphone and text typed into fields stay out of the recording.
- **Deleted after 48 hours**: The tester can delete their recording right after the test, and the developer deletes it with one button in the studio.
- **On our own server**: Recordings are stored on the klyo server, not in another company's cloud. One test takes at most 48 MB.
- **Aged 16 and over**: Agreeing to the test confirms that the tester is at least 16 years old.

The full rules are in the [privacy policy](https://games.klyo.pl/privacy/), in the part about game tests.

## Run your first test today

Create a developer account, upload your game and make a test link under Results. You will see the first recording a few minutes after someone plays.

[Open the developer studio](https://dev.klyo.pl/)

[AI assistants and MCP](https://games.klyo.pl/mcp/)

---

Source: https://games.klyo.pl/playtesting/ · Built and run by klyo, a Polish technology company (Łódź) · Contact: kontakt@klyo.pl · Index for language models: https://games.klyo.pl/llms.txt
