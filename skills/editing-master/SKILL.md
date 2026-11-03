---
name: editing-master
description: Make a hooking product video step by step with the user (how-to, demo, launch teaser, explainer) with Claude Code and HyperFrames, from a codebase, a link to a live app or website, screenshots, a screen recording, or just a description. Asks what video the user wants, shows a menu of video skills and recommends one for the project (HyperFrames by default; also onetake, Collage B-roll, Clawd Animation, Lemo Opuscar, explainroo, Manim, Remotion and more), offers a fast track (three stops before render) or step by step, says how long each part takes, plays voice, music and sound samples to choose by ear, writes a script for approval, builds a preview with camera zooms, one-word screens, transitions, cursor clicks, music and subtitles, and renders only after approval. Use when the user asks for a video, demo video, product video, walkthrough video, teaser or explainer of their product, app, website or project.
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

**Tools.** By default, build with the HyperFrames skills (`hyperframes`, `hyperframes-cli`,
`hyperframes-registry`) and use `media-use` for voice, music and sound effects. If they are
missing, tell the user the install commands (see README) and stop. Say in one line which
skills you will use before you start.

**Starter.** `starter/` is a working HyperFrames project with the building blocks below
(one-word screens, chapter card, camera focus with cursor click, transitions, outro). Copy
it into a new `video/` folder and adapt it; do not start from a blank page.

**Engine.** Everything this skill builds (one-word screens, hook and chapter cards, camera,
cursor, starter) is HyperFrames, and HyperFrames is the default. Other video skills give
other kinds of video (one-shot camera, paper collage, watercolour, 2D cartoons, narrated
whiteboard explainers, maths animation, React motion graphics, stock-footage montages, app
animations, shorts cut from long recordings); each has its own workflow. See
`references/video-skills.md` and step 2.

## The golden rule: nothing without the user

Anything that will be heard or seen in the video (voice, music, sound effects, script,
look) is shown or played to the user before the film is final, and **nothing is rendered
before the user approves the preview**. How often you stop to ask depends on the mode the
user picks: fast track or step by step.

## Two modes: fast track or step by step

The machine work is quick (≈ 1 min to voice a 2-minute script, ≈ 1 min to find music,
≈ 3 min to render a 2-minute film). What makes a video slow is the number of times the
user has to stop and answer. In your first message, offer the two modes and recommend fast
track:

| | Fast track (recommended) | Step by step |
|---|---|---|
| Stops before render | 3, then "render" | about 11, one per step |
| Questions | all in one message, each with a default | one step at a time |
| Samples | voice, music, mix and effects in one listening pack | voice, music, effects in separate rounds |
| Best for | most videos, users who trust the defaults | users who want to steer every detail |

The user can switch at any time ("slow down", "go faster").

### Fast track: three stops, then render

Steps 1–11 below still say how to do each piece; fast track groups them into three stops
and does the machine work in between without asking.

**Stop 1 · The plan** (one message, steps 1–3). Ask the brief questions (step 1), show the
video-skill menu with your recommendation (step 2), and ask the style questions with your
recommended answer for each (step 3, subtitles included). End with: "Answer what you want
to change, or say **use your picks**." One reply settles all of it. Repeat the final plan
back in a few lines, with the total time to the preview, and go on without another stop.

**Between stops 1 and 2, without asking:** study the product (step 7), write the script
(step 8), and prepare the listening pack: the hook line in 3 voices, 15–20 s samples of
3 music tracks, a voice + music mix at the planned level using your recommended voice and
track, and the sound-effect reel (steps 4–6). Say how long this takes before you start
(usually a few minutes), and run the voice and music work in parallel with the study.

**Stop 2 · Script, screens and sounds** (one message). Send the script table, the list of
steps the video shows with one rebuilt screen (a snapshot), and the listening pack, with
your recommended voice, track and effects marked. Ask for one reply: "Approve the script
and the screens, and pick a voice, a track and the effects (or say **use your picks**)."

**Between stops 2 and 3, without asking:** voice the approved script, transcribe it, build
the preview (step 9) and check it.

**Stop 3 · Preview.** Send the preview link with timestamps. The full narration, music and
effects are heard here for the first time together. Apply changes and send it again until
the user approves. Preview rounds are not counted as extra stops.

**Render** only when the user says "render" (step 10), then hand over (step 11).

If the user says "just do it" in fast track, use your recommended picks at stops 1 and 2,
still send the script, screens and listening pack so they can listen, and go on building
the preview without waiting. Stop 3 is never skipped: no render without an approved
preview.

### Step by step

Go through steps 1–11 one at a time. Each step: say how long it will take, do it, show the
result, ask "OK to continue?", wait. Never chain two steps without the user's go-ahead;
if the user says "just do it", offer to switch to fast track instead.

### In both modes

Start by telling the user the stops and rough times (see "Time budget"). Before any wait
longer than a few seconds, say how long it will take. Use the measured times in "Time
budget"; when there is no measured number, say so ("several minutes on a CPU") instead of
inventing one.

## The steps

### 1 · What video do you want? (always ask first)

Even if the user only said "make a video", ask, with examples and a recommendation (in fast
track, in the same message as steps 2 and 3, along with the mode question):

- What is it for? (how to use it, what it does, a launch teaser, a feature tour, an ad…)
- Who watches it? (new users, customers, investors, a team…)
- Length and format: 30 s / 60 s / 2 min; 16:9 or 9:16 vertical.
- The one message they should remember.
- What do you have about the product: a codebase, a link, screenshots, a recording, or only
  a description? (Skip if it is obvious, e.g. you are in its repo.)

Step by step: repeat the brief back in three lines and wait for "yes".

### 2 · Which video skill? (recommend one, then ask)

Read `references/video-skills.md`, then show the user its menu as one table: each skill's
name, what the video looks like, what it is best for, how long it takes and what it costs,
in words someone new to it understands. Group it as "build a video from scratch" (HyperFrames,
onetake, Collage B-roll, Clawd Animation, Lemo Opuscar, explainroo, iart explainer skills,
Manim, Remotion, Animate, Guizang product video, OpenMontage, Lottie) and "edit a video you
already have" (Clipify, Cut Video).

Then recommend **one** for this project from the "Which one for which project?" table, in
one or two lines: why it fits the brief, its cost and licence, its time. Name a close second
if there is one. Flag licences that matter for company videos (onetake, Remotion, AGPL
skills) and anything that needs a paid key, a GPU or macOS.

Say that this skill's building blocks and the starter are HyperFrames; with another engine,
follow that skill's own workflow, and keep this skill's mode and rules (fast track or step
by step, let the user hear everything, preview before render). If the chosen skill is not installed,
give its install command and wait.

### 3 · Style questions (one message, options + recommendation for each)

1. Presenter: none, the logo pulsing with the voice in a round corner frame (free), or a
   talking avatar (paid).
2. Cursor and click sounds on every action? (recommend yes)
3. Camera: light / medium / strong zooms (recommend medium).
4. Kinetic type: one-word screens for the hook, chapter cards, a "this is the easiest part"
   hook card? Which moments? (Show `docs/img` examples or describe them.)
5. Subtitles: none, **burned into the video**, or **separate subtitle files**? Then which
   languages?
   - Burned in: always visible, on every platform and with sound off (social feeds, ads),
     but one language only and a change means a re-render.
   - Separate files: `.srt` (players, YouTube, LinkedIn) and/or `.vtt` (web players), one
     per language, editable by hand, viewers switch them on and off; a platform or player
     that ignores them shows none.
   - Recommend burned in for short social clips that autoplay muted, separate files for
     how-tos and anything in several languages. Both is fine (burn in the main language,
     ship files for all).
6. Brand: read colours, logo and fonts from the source; only ask what is missing, and show
   the palette you will use.

### 4 · Voice: listen, then choose

Say the time first: free Kokoro voices take ≈ 5 s per line (mostly loading the model) and
≈ 1 min for a whole 2-minute script; paid voices are fast but need an account and an API key.

1. Offer the tools: free on this machine (Kokoro, `npx hyperframes tts`, no account) or paid
   (HeyGen, ElevenLabs: say what each needs and costs).
2. Voice the **same** hook line in 3 voices (e.g. energetic US male, warm US female, calm
   British male) and send the files so the user can listen.
3. Wait for the choice. Offer more samples or another speed if none fits.

### 5 · Music: listen, then choose

Say the time first: a free CC track takes ≈ 1 min to find and download, plus a few seconds
per sample cut; generating music locally (MusicGen) is free but slow on a CPU, several
minutes per clip; a paid catalog (HeyGen music) is instant but needs an account.

1. Find 3 candidate tracks that fit the mood (free CC tracks first; say the licence and
   whether a credit line is needed).
2. Cut a 15–20 s sample of each from the part you would use, and send them.
3. Wait for the choice (or "no music"). Then say the level you will use (≈ 16 % under the
   voice) and send a 15 s mix of voice + music so the balance can be heard.

### 6 · Sound effects: listen, then confirm

Send the click, pop, whoosh and typing sounds you plan to use (one short file each, or one
file with all of them in a row). Ask: keep, change, or no effects.

### 7 · Study the product

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

### 8 · Script (wait for "approved")

A scene table: time · on screen · voiceover · effect (one-word screen, zoom, hook card…). Rules in `references/kinetic-type-and-hooks.md`
(hook in 5 s, one idea per scene, 15–20 words per scene, every sentence shown on screen,
an attention reset every 20–30 s). Send it and wait for "approved"; change it as often as
asked. Voice the lines only after approval (≈ 1 min for a 2-minute script with Kokoro; say
so), then send the full narration to listen to and ask before building on it.

### 9 · Build the preview

- Voice: one file per line; transcribe the full narration (`npx hyperframes transcribe`,
  ≈ 20 s for a 4-minute film) for word times. Every action lands on its word (word time +
  0.2 s).
- Subtitles as chosen in step 3: burned-in captions as a HyperFrames layer (visible in the
  preview), or SRT/VTT files from the transcript. See `references/music-sfx-subtitles.md`.
- Camera, transitions, cursor: `references/transitions-and-camera.md`.
- Pacing and reading time: `references/pacing-and-voice.md`.
- Music, effects, subtitles, cover: `references/music-sfx-subtitles.md`.
- Check: `npx hyperframes check`, then `npx hyperframes snapshot --at …` at every step and
  cut; look at the frames and fix overlaps, cut-off UI and anything off its word.

Start the preview (`npx hyperframes preview`), send the link with timestamps to look at,
and wait. Apply changes in the preview, say what changed, and send it again; repeat until
the user says it is approved.

### 10 · Render (only when the user says "render")

Say how long it will take (plain HyperFrames ≈ 1.3 s per second of video on a CPU, so a
2-minute film takes about 3 minutes; other engines in `references/video-skills.md`), then
render at delivery quality, normalise to −16 LUFS (peaks under −1 dBTP), pull frames from
the finished file to confirm it matches the preview. Send the file to watch.

### 11 · Hand over

One output folder: the .mp4, cover (with and without a play button), the script, and a
short README (credits, how to re-render). Subtitles as chosen in step 3:

- Burned in: they are in the .mp4; say which language, and that a change means editing the
  captions and re-rendering. Add the matching .srt too if the user may want it later.
- Separate files: one .srt and/or .vtt per language next to the .mp4 (`video.en.srt`,
  `video.fr.vtt`…), with a README line on editing them by hand and uploading them to the
  platform or player.
Do not decide where the video is published, and do not commit or push unless asked.

## Time budget (tell the user)

| Step | Typical time on a laptop |
|---|---|
| Voice, one line (Kokoro) | ≈ 5 s, mostly loading the model |
| Voice, whole 2-min script (Kokoro) | ≈ 1 min |
| Voice, paid (HeyGen, ElevenLabs) | fast; needs an account and an API key |
| Find and download a free CC music track | ≈ 1 min, plus a few seconds per sample cut |
| Generate music locally (MusicGen) | slow on a CPU: several minutes |
| Subtitles (transcribe a 4-min film) | ≈ 20 s |
| Render, plain HyperFrames | ≈ 1.3 s per second of video (2:11 film in 2 min 46 s) |
| Render, other engines | see `references/video-skills.md` (3.5–21 s per second) |
| Review loops with the user | most of the time |

## Hard rules

- Ask "what video do you want?" first, every time, with the mode question (fast track
  recommended) and the video-skill recommendation.
- Fast track: three stops (plan; script, screens and sounds; preview), then "render".
  Step by step: ask before every next step. In both, say how long things take.
- Ask burned-in or separate subtitle files; never assume.
- The user hears every voice, music track and sound effect before the film is final (as
  samples first; in fast track with "just do it", at the latest in the preview).
- Script approval before voicing it; preview approval before rendering.
- One click = one state change. Never flip a switch twice for one click.
- Readable on screen: hold text at least 0.5 s + 0.3 s per word after it finishes appearing.
- Never use the same transition for every cut; never an effect without a reason.
- Never render to "check": that is what the preview and snapshots are for.

See `references/checklist.md` for the full list of mistakes this skill prevents.
