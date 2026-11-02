---
name: editing-master
description: Make a hooking product video step by step with the user (how-to, demo, launch teaser, explainer) with Claude Code and HyperFrames, from a codebase, a link to a live app or website, screenshots, a screen recording, or just a description. Asks what video the user wants, asks before every step, plays voice, music and sound samples to choose by ear, writes a script for approval, builds a preview with camera zooms, one-word screens, transitions, cursor clicks, music and subtitles, and renders only after approval. Use when the user asks for a video, demo video, product video, walkthrough video, teaser or explainer of their product, app, website or project.
---

# Editing Master

Turn a product into a short, lively video. The user gives one line ("how to use it,
2 minutes") and whatever they have about the product; you ask, they choose, you build,
they approve, you render.

**What the user can start from** (any one is enough; more is better):

| Source | How you use it |
|---|---|
| A codebase (the current folder or a path) | Read the UI source and rebuild the real screens. |
| A link to the live app or website | `npx hyperframes capture <url> --json` for screenshots, colours, fonts and copy; rebuild the screens from them. Ask for a test login if pages sit behind sign-in; never use real credentials. |
| Screenshots or a screen recording | Rebuild each screen from the images; use recording clips as B-roll inside a framed device. |
| Only a description | Design clean, plausible screens in the brand colours from the description, and say so in the script. |

**Tools.** Build with the HyperFrames skills (`hyperframes`, `hyperframes-cli`,
`hyperframes-registry`) and use `media-use` for voice, music and sound effects. If they are
missing, tell the user the install commands (see README) and stop. Say in one line which
skills you will use before you start.

**Starter.** `starter/` is a working HyperFrames project with the building blocks below
(one-word screens, chapter card, camera focus with cursor click, transitions, outro). Copy
it into a new `video/` folder and adapt it; do not start from a blank page.

## The golden rule: nothing without the user

Every step ends with a question and waits for a clear yes. Never chain two steps without
the user's go-ahead. Anything that will be heard or seen in the video (voice, music, sound
effects, script, look) is shown or played to the user **before** it goes in. If the user
says "just do it", still show each result and ask before moving on.

## The work loop

Start by telling the user the steps and rough times (see "Time budget"), then go step by
step. Each step: do it, show the result, ask "OK to continue?", wait.

### 1 · What video do you want? (always ask first)

Even if the user only said "make a video", ask, with examples and a recommendation:

- What is it for? (how to use it, what it does, a launch teaser, a feature tour, an ad…)
- Who watches it? (new users, customers, investors, a team…)
- Length and format: 30 s / 60 s / 2 min; 16:9 or 9:16 vertical.
- The one message they should remember.
- What do you have about the product: a codebase, a link, screenshots, a recording, or only
  a description? (Skip if it is obvious, e.g. you are in its repo.)

Repeat the brief back in three lines and wait for "yes".

### 2 · Style questions (one message, options + recommendation for each)

1. Presenter: none, the logo pulsing with the voice in a round corner frame (free), or a
   talking avatar (paid).
2. Cursor and click sounds on every action? (recommend yes)
3. Camera: light / medium / strong zooms (recommend medium).
4. Kinetic type: one-word screens for the hook, chapter cards, a "this is the easiest part"
   hook card? Which moments? (Show `docs/img` examples or describe them.)
5. Subtitles: which languages?
6. Brand: read colours, logo and fonts from the source; only ask what is missing, and show
   the palette you will use.

### 3 · Voice: listen, then choose

1. Offer the tools: free on this machine (Kokoro, `npx hyperframes tts`, no account) or paid
   (HeyGen, ElevenLabs: say what each needs and costs).
2. Voice the **same** hook line in 3 voices (e.g. energetic US male, warm US female, calm
   British male) and send the files so the user can listen.
3. Wait for the choice. Offer more samples or another speed if none fits.

### 4 · Music: listen, then choose

1. Find 3 candidate tracks that fit the mood (free CC tracks first; say the licence and
   whether a credit line is needed).
2. Cut a 15–20 s sample of each from the part you would use, and send them.
3. Wait for the choice (or "no music"). Then say the level you will use (≈ 16 % under the
   voice) and send a 15 s mix of voice + music so the balance can be heard.

### 5 · Sound effects: listen, then confirm

Send the click, pop, whoosh and typing sounds you plan to use (one short file each, or one
file with all of them in a row). Ask: keep, change, or no effects.

### 6 · Study the product

From whatever the user gave you, list the 5–8 things a user actually does, in order:

- **Codebase:** read the README, UI source (markup, CSS tokens, copy, icons) and brand
  assets; rebuild the real UI from its source.
- **Link:** capture the pages that matter (`npx hyperframes capture <url> --json`), walk
  the main flow in a browser if needed, and rebuild the screens from the captures (same
  labels, colours, radii, spacing). Do not screen-record a live site into the film unless
  the user asks.
- **Screenshots / recording:** rebuild each screen from the images; keep recording clips
  for B-roll in a device frame.
- **Description only:** design the screens from the description and the brand; keep them
  simple and mark them as illustrative in the script.

Never invent features the product does not have. Unknown or private names become neutral
("Model A, B, C"); sample secrets are obviously fake and split in source (`ghp_<i></i>…`).
If the look is unclear, ask for a screenshot instead of guessing.

Show the user the list of steps you will show in the video, and one rebuilt screen (a
snapshot), and ask: "Is this how it looks, and are these the right steps?" Wait.

### 7 · Script (wait for "approved")

A scene table: time · on screen · voiceover · effect (one-word screen, zoom, hook card…). Rules in `references/kinetic-type-and-hooks.md`
(hook in 5 s, one idea per scene, 15–20 words per scene, every sentence shown on screen,
an attention reset every 20–30 s). Send it and wait for "approved"; change it as often as
asked. Voice the lines only after approval, then send the full narration to listen to and
ask before building on it.

### 8 · Build the preview

- Voice: one file per line; transcribe the full narration (`npx hyperframes transcribe`)
  for word times. Every action lands on its word (word time + 0.2 s).
- Camera, transitions, cursor: `references/transitions-and-camera.md`.
- Pacing and reading time: `references/pacing-and-voice.md`.
- Music, effects, subtitles, cover: `references/music-sfx-subtitles.md`.
- Check: `npx hyperframes check`, then `npx hyperframes snapshot --at …` at every step and
  cut; look at the frames and fix overlaps, cut-off UI and anything off its word.

Start the preview (`npx hyperframes preview`), send the link with timestamps to look at,
and wait. Apply changes in the preview, say what changed, and send it again; repeat until
the user says it is approved.

### 9 · Render (only when the user says "render")

Say how long it will take, then render at delivery quality, normalise to −16 LUFS (peaks under −1 dBTP), pull frames from
the finished file to confirm it matches the preview. Send the file to watch.

### 10 · Hand over

One output folder: the .mp4, cover (with and without a play button), one .vtt per
language, the script, and a short README (edit subtitles by hand, re-render, credits).
Do not decide where the video is published, and do not commit or push unless asked.

## Time budget (tell the user)

| Step | Typical time on a laptop |
|---|---|
| Voice, one line (Kokoro) | ≈ 5 s |
| Voice, whole 2-min script | ≈ 1 min |
| Find and download a free music track | ≈ 1 min |
| Subtitles (transcribe a 4-min film) | ≈ 20 s |
| Render, plain HyperFrames | ≈ 1.3 s per second of video |
| Render, heavy looks (motion blur, watercolour) | 15–20 s per second of video |
| Review loops with the user | most of the time |

## Hard rules

- Ask "what video do you want?" first, every time.
- One step at a time; ask before every next step.
- The user hears every voice, music track and sound effect before it goes in.
- Script approval before voicing it; preview approval before rendering.
- One click = one state change. Never flip a switch twice for one click.
- Readable on screen: hold text at least 0.5 s + 0.3 s per word after it finishes appearing.
- Never use the same transition for every cut; never an effect without a reason.
- Never render to "check": that is what the preview and snapshots are for.

See `references/checklist.md` for the full list of mistakes this skill prevents.
