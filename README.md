# Editing Master

A Claude Code skill that turns your product into a short, hooking video: one-word screens,
hook cards, camera zooms, cursor clicks, transitions, a voiceover, music and subtitles.
Claude asks what you want, lets you hear every voice and track before it goes in, asks
before every step, and renders only when you approve.

![One-word screens](docs/img/one-word-screens.gif)

Works from whatever you have:

- **a codebase** (the folder you are in),
- **a link** to your live app or website,
- **screenshots or a screen recording**,
- or **just a description**.

## Install

As a plugin (recommended):

```bash
claude plugin marketplace add Maher-bouchrara/Editing-Master-skill
claude plugin install editing-master@editing-master
```

Inside a Claude Code session, the same with `/plugin marketplace add …` and
`/plugin install …`. Or ask Claude in the chat:
*"Install the editing-master skill from github.com/Maher-bouchrara/Editing-Master-skill."*

It builds on HyperFrames, so install that too:

```bash
claude plugin marketplace add heygen-com/hyperframes
claude plugin install hyperframes@hyperframes
```

Restart Claude Code after installing.

## Use

Open Claude Code on your project (or anywhere, if you have a link or screenshots) and ask:

```text
Make a video for this project.
```

Claude asks **what video you want** first: what it's for, who watches it, how long, the one
message to remember. You can also say it right away:

```text
A 30-second vertical teaser of https://my-app.example.com, for new customers.
```

Then it goes **one step at a time and asks before each next step**. Nothing goes into the
video that you haven't seen or heard:

1. **What video?** It repeats your brief back; you say yes.
2. **Style.** Presenter, cursor clicks, zooms, one-word screens, subtitles, brand colours;
   each with options and a recommendation.
3. **Voice: listen, then choose.** The same line in 3 voices.
4. **Music: listen, then choose.** 15–20 s samples of 3 tracks, then a voice + music mix.
5. **Sound effects: listen, then confirm.** Clicks, pops, whooshes.
6. **The screens and steps.** It shows a rebuilt screen and the steps it will show.
7. **Script.** You approve it, then listen to the full voiceover.
8. **Preview.** Ask for changes in plain words ("slower here", "zoom on the popup",
   "subtitles smaller"). Repeat until you love it.
9. **Say "render".**

![The seven steps](docs/img/step-by-step.jpg)

## What it does for you

### Hooks and one-word screens

Full-colour screens, one or two words per beat, each on its spoken word.

![One-word screens, still frames](docs/img/one-word-grid.jpg)

![Tips as one-word screens](docs/img/one-word-tips.gif)

| Hook card before the easiest step | Chapter card for the main part |
|---|---|
| ![Hook card](docs/img/hook-card.jpg) | ![Chapter card](docs/img/chapter-card.jpg) |

| Pattern break | Brand reveal |
|---|---|
| ![Pattern break](docs/img/pattern-break.jpg) | ![Brand reveal](docs/img/brand-reveal.jpg) |

### Camera, cursor and step chips

Push in on the control being named, click on the word, hold, pull back.

| Step chip and real UI | Zoom on the action |
|---|---|
| ![Step chip](docs/img/camera-step-chip.jpg) | ![Zoom on the action](docs/img/zoom-on-action.jpg) |

| Readable commands | A decision moment |
|---|---|
| ![Camera zoom on commands](docs/img/camera-zoom.jpg) | ![Human in the loop](docs/img/human-in-the-loop.jpg) |

### Voice, music, subtitles

- Free voices on your laptop (Kokoro), or paid (HeyGen, ElevenLabs).
- One quiet music bed (≈ 16 % under the voice), effects only on visible actions.
- Subtitles in any languages, as separate tracks you can edit by hand.

## How long it takes

| Step | Typical time on a laptop |
|---|---|
| One voice line | ≈ 5 s |
| A whole 2-minute script | ≈ 1 min |
| Find a free music track | ≈ 1 min |
| Subtitles for a 4-minute film | ≈ 20 s |
| Render (plain HyperFrames) | ≈ 1.3 s per second of video |
| Your review loops | most of the time |

## What's inside

```
skills/editing-master/
  SKILL.md                         the workflow Claude follows
  references/
    kinetic-type-and-hooks.md      one-word screens, hook and chapter cards, script rules
    transitions-and-camera.md      focus camera, cursor, six transitions and when to use them
    pacing-and-voice.md            reading time, rhythm, voices and samples
    music-sfx-subtitles.md         music sources and levels, effects, subtitles, cover
    checklist.md                   the mistakes each rule prevents
  starter/                         a working HyperFrames project with all the building blocks
```

Try the starter on its own:

```bash
cd skills/editing-master/starter
npx hyperframes preview
```

## Examples

The frames above come from two videos made with this workflow: a how-to video for
VamiGuard, and "Video with Claude Code", a video about the method itself.

## Licence

MIT
