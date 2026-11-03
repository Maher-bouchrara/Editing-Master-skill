# Which video skill?

There are many Claude Code video skills, and each gives a different kind of video. This
skill's own building blocks (one-word screens, hook and chapter cards, focus camera, cursor
clicks, transitions, the starter) are **HyperFrames**, so HyperFrames is the default. Every
other skill below is an alternative the user can pick; each has its own workflow, which you
follow instead of the HyperFrames steps. Keep this skill's rules with any of them: ask
before every step, let the user hear voice, music and effects first, get the script
approved, preview before render.

## How to present the choice (step 2)

1. Show the menu below as one table: name, what the video looks like, best for, time, cost.
   Every row must be clear to someone who has never heard of the skill.
2. Recommend **one** for this user's project, in one or two lines: why it fits the brief,
   what it costs, how long it takes. Name one alternative if there is a close second.
3. Ask, and wait. If the chosen skill is not installed, give its install command and wait.
4. If the user is unsure, recommend HyperFrames: it is free, fast, and everything in this
   skill works with it.

## Which one for which project?

| The project is… | Recommend | Close second |
|---|---|---|
| A how-to, demo or feature tour of a real app or website | **HyperFrames** | Remotion (if the team already uses React) |
| A software update or release promo built from the product's own UI | **HyperFrames** | Guizang product video |
| A launch teaser that feels like one continuous camera move | **onetake** | HyperFrames |
| A narrated explainer with drawings appearing as the voice speaks | **explainroo** | iart explainer skills |
| A whiteboard, diagram or isometric explainer, or many personalised videos from a data table | **iart explainer skills** | explainroo |
| Maths, algorithms, data science, research: equations and graphs | **Manim** | iart diagram animation |
| A playful, handmade social clip or B-roll | **Collage B-roll** | Animate (cut paper style) |
| A warm, storybook, hand-painted feel | **Clawd Animation** | Animate (sketchbook style) |
| A short character story or 2D cartoon from a brief | **Lemo Opuscar** | Animate |
| A stylised short in a strong look (riso print, pixel art, crosshatch ink…) | **Animate** | Collage B-roll |
| A documentary-style montage, trailer or dubbed video from stock and archive footage | **OpenMontage** | none |
| An animation to put inside a website or mobile app (not an MP4) | **Lottie** | none |
| Turning a long recording (webinar, podcast, talk) into vertical shorts | **Clipify** | none |
| Cleaning a talking-head recording (silences, "um", retakes) | **Cut Video** | none |

## The menu

Time columns: **our render** times were measured by us on one laptop, render only.
**15 s promo, start to finish** is a third-party test by
[awesome-claude-video-skills](https://github.com/zhuyansen/awesome-claude-video-skills),
with the same brief for every skill, including the agent's writing time. Where neither
exists, say "not measured" and do not guess.

### Build a video from scratch

| Skill | What the video looks like | Best for | Time | Licence / cost |
|---|---|---|---|---|
| **HyperFrames** (default) | Crisp motion design: real UI rebuilt in HTML, camera zooms, cursor clicks, one-word screens, captions | Product walkthroughs, how-tos, feature tours | Render ≈ 1.3 s per second of video (2:11 film in 2 min 46 s), CPU | Apache-2.0, free |
| **onetake** | One unbroken camera move gliding through the product, with motion blur | One-shot launch films and teasers | Render ≈ 18 s per second (14.5 s clip in 4 min 21 s), CPU | PolyForm Noncommercial; business use needs onetake Pro |
| **Collage B-roll** | Stop-motion paper collage: cut-out shapes and textures that jump frame to frame | Playful B-roll, social clips | Render ≈ 3.5 s per second (10 s clip in 35 s) | MIT; needs a paid Gemini API key |
| **Clawd Animation** | Hand-drawn watercolour animation, soft and painterly | Warm, storybook brand films | Render ≈ 21 s per second (15 s clip in 5 min 21 s), GPU | MIT, free; needs a GPU |
| **Lemo Opuscar** | Flat 2D cartoon with characters and scenes, written from a brief | Short story films, character explainers | 16 s clip rendered in 12 s, plus ≈ 8 min of agent work | MIT, free |
| **explainroo** | A narrated whiteboard-style explainer: drawings appear on the word the voice says; 6 looks (paper, clean, chalk, blueprint, midnight, editorial) | Explainers, product concepts, YouTube videos | 15 s promo ≈ 2 min start to finish (fastest in the test) | MIT, free; local Kokoro voice, no account |
| **iart explainer skills** | Five skills: narrated explainers, whiteboard draw-on, animated diagrams and charts, isometric 2.5D scenes, "Wrapped"-style recaps in bulk | Explainers, data stories, personalised videos from a spreadsheet | Not measured | MIT, free; no keys listed |
| **Manim** | 3Blue1Brown style: equations, graphs and shapes that transform smoothly, on a dark background, with narration | Maths, algorithms, technical and research explainers | Not measured | MIT, free; needs Python and LaTeX |
| **Remotion** (official skills) | Motion graphics written as React code: any layout, charts, text, video clips | Teams who know React; data-driven or templated videos | 15 s promo ≈ 4.5 min start to finish | Remotion is free for individuals, non-profits and companies of up to 3 people; bigger companies need a paid company licence |
| **Animate** | Short procedural canvas animations in a chosen style: cut paper, crosshatch ink, riso print, sketchbook, pixel art, isometric line art, maths style; can copy a style from your images | Stylised shorts, histories, little stories, product reels | Not measured | MIT, free |
| **Guizang product video** | A 45–60 s software-update promo built from the product's real components: title cards, feature close-ups, full-workspace views, cut to a music beat (default language Chinese) | Release and update promos for a software product with source code | 15 s promo ≈ 8.6 min start to finish | AGPL-3.0, with some bundled parts under Business Source License 1.1 |
| **OpenMontage** | A full production pipeline: documentary montages from free stock and archive footage, trailers, talking heads, screen demos, dubbing; renders with Remotion, HyperFrames or FFmpeg | Documentary-style or footage-heavy videos, localisation | 15 s promo ≈ 8.6 min start to finish | AGPL-3.0; free with no keys; optional paid AI generators ≈ $1–5 per video |
| **Lottie** | A Lottie JSON animation (not an MP4) that plays inside a website or iOS/Android/Flutter app, or opens in After Effects | Animated icons, onboarding and empty-state animations | 15 s promo ≈ 5.6 min start to finish | MIT, free |

### Edit a video you already have

| Skill | What it does | Best for | Time | Licence / cost |
|---|---|---|---|---|
| **Clipify** | Finds 3–5 strong moments in a long video, reframes 16:9 to 9:16 so the camera follows the speaker, burns in word-by-word captions | Webinars, podcasts, talks → vertical shorts | ≈ 20 s of work per 20 s clip on Apple Silicon (author's figure) | MIT, free, local; built for macOS |
| **Cut Video** | Removes silences, filler words and retakes from a recording, keeps laughs and real pauses, re-checks the result | Talking-head and screen-recording clean-up before editing | A 7-min 4K interview cut in ≈ 30 s on Apple Silicon (author's figure) | MIT, free, local; built for macOS |

Clipify and Cut Video target macOS (Apple hardware decoding). On Windows or Linux they need
the `-hwaccel videotoolbox` flags removed, which their authors do not support; say so. They
combine well with HyperFrames: clean a screen recording with Cut Video, then use it as
B-roll inside a HyperFrames film.

## Install and details

Never type an API key for the user; ask them to set it themselves.

### HyperFrames

- Repo: [heygen-com/hyperframes](https://github.com/heygen-com/hyperframes). Apache-2.0.

  ```bash
  claude plugin marketplace add heygen-com/hyperframes
  claude plugin install hyperframes@hyperframes
  ```

- HTML compositions rendered to video on a CPU. What `starter/` and every reference in this
  skill use.

### onetake

- Repo: [feitangyuan/onetake](https://github.com/feitangyuan/onetake). PolyForm
  Noncommercial: say before recommending it for a company video that business use needs
  onetake Pro.

  ```bash
  git clone https://github.com/feitangyuan/onetake.git ~/.claude/skills/onetake
  pip install playwright numpy scipy Pillow matplotlib fonttools brotli
  ```

- Slow render because of motion blur; keep it short.

### Collage B-roll

- Repo: [pyang5166/gbro-collage-broll](https://github.com/pyang5166/gbro-collage-broll). MIT.
  Needs a paid Gemini API key.

  ```bash
  git clone https://github.com/pyang5166/gbro-collage-broll.git ~/.claude/skills/gbro-collage-broll
  ```

### Clawd Animation

- Repo: [JohnHeibel/ClaudeAnimationBase](https://github.com/JohnHeibel/ClaudeAnimationBase). MIT.

  ```bash
  git clone https://github.com/JohnHeibel/ClaudeAnimationBase.git
  cd ClaudeAnimationBase
  npm install
  ```

  Then ask Claude in that folder: *"Read ANIMATION_GUIDE.md, then make …"*. Needs a GPU.

### Lemo Opuscar

- Repo: [lemomo-ai/lemo-opuscar](https://github.com/lemomo-ai/lemo-opuscar). MIT.

  ```bash
  claude plugin marketplace add lemomo-ai/lemo-opuscar
  claude plugin install lemo-opuscar@lemolab
  ```

### explainroo

- Repo: [vincentsch/explainroo](https://github.com/vincentsch/explainroo). MIT.

  ```bash
  git clone https://github.com/vincentsch/explainroo.git
  cd explainroo
  npm install
  node bin/explainroo.js doctor --fetch
  ```

  Then start Claude Code in that folder and ask for a video. Needs Node 20.11+, ffmpeg and
  Chrome; the first setup downloads ≈ 400 MB of voice and timing models. No GPU. Ships
  .srt and .vtt subtitles, a cover and YouTube chapters; 16:9, 9:16, 4:5 and square.
  Optional paid extras: ElevenLabs voice, AI illustrations through OpenRouter.

### iart explainer skills

- Repo: [iart-ai/explainer-video-skills](https://github.com/iart-ai/explainer-video-skills). MIT.

  ```bash
  claude plugin marketplace add iart-ai/explainer-video-skills
  claude plugin install explainer-video-skills
  ```

  Skills: `explainer-video` (30–90 s narrated short), `whiteboard-animation`,
  `diagram-animation`, `isometric-animation`, `wrapped-video` (many 9:16 videos from one
  template and a data table).

### Manim

- Repo: [Yusuke710/manim-skill](https://github.com/Yusuke710/manim-skill). MIT.

  ```bash
  git clone https://github.com/Yusuke710/manim-skill
  cd manim-skill
  uv sync
  ```

  Then link `skills/manim-skill` into `~/.claude/skills/manim-skill`. Needs Python, ffmpeg,
  cairo and LaTeX (the README gives macOS steps; on Windows use MiKTeX). Local Kokoro
  narration and synced subtitles are on by default.

### Remotion

- Repo: [remotion-dev/skills](https://github.com/remotion-dev/skills), official skills from
  Remotion.

  ```bash
  npx skills add remotion-dev/skills
  ```

- Licence: Remotion is free for individuals, non-profits and for-profit companies with up to
  3 employees; others need a company licence ([remotion.pro/license](https://remotion.pro/license)).
  Ask the user which applies before recommending it for a company video.

### Animate

- Repo: [cth9191/animate](https://github.com/cth9191/animate). MIT.

  ```bash
  claude plugin marketplace add cth9191/animate
  claude plugin install animate@animate
  npm i -g playwright && npx playwright install chromium
  ```

  Run with `/animate:animate`. Needs Node 18+, ffmpeg; Python with `faster-whisper` for
  voice-overs. It asks about story, look and storyboard before animating, and can time cuts
  to the user's own music track.

### Guizang product video

- Repo: [op7418/guizang-product-video-skill](https://github.com/op7418/guizang-product-video-skill).
  AGPL-3.0, with parts in `assets/fallback/` under Business Source License 1.1; commercial
  terms in its `COMMERCIAL_LICENSING.md`. Mention this for company use.

  ```bash
  git clone https://github.com/op7418/guizang-product-video-skill.git ~/.claude/skills/guizang-product-video-skill
  ```

  Needs Node 22+, Python 3.9+, FFmpeg and Playwright Chromium, plus the product's own repo.
  Default is a 45–60 s horizontal film in Chinese; ask for English.

### OpenMontage

- Repo: [calesthio/OpenMontage](https://github.com/calesthio/OpenMontage). AGPL-3.0.

  ```bash
  git clone https://github.com/calesthio/OpenMontage.git
  cd OpenMontage
  make setup
  ```

  Needs Python 3.10+, FFmpeg, Node 18+ (22+ for HyperFrames). Works with no paid keys
  (Piper voice, archive and stock footage); optional paid generators (Kling, Runway,
  ElevenLabs, Suno, HeyGen…) cost about $1–5 per video, with a default $10 budget cap.
  Free local video generation needs a GPU.

### Lottie

- Repo: [diffusionstudio/lottie](https://github.com/diffusionstudio/lottie). MIT.

  ```bash
  npx skills add diffusionstudio/lottie
  ```

  Output is Lottie JSON for `lottie-web`, iOS, Android, Flutter or React Native, or import
  into After Effects. Not an MP4: say so if the user wants a video file.

### Clipify

- Repo: [louisedesadeleer/clipify](https://github.com/louisedesadeleer/clipify). MIT.

  ```bash
  git clone https://github.com/louisedesadeleer/clipify.git ~/.claude/skills/clipify
  ```

  Run with `/clipify`. Needs ffmpeg (libx264), `openai-whisper`, Python 3 with numpy. Output
  in `clipify_out/` next to the source video; 9:16, 16:9 or 1:1.

### Cut Video

- Repo: [louisedesadeleer/cut-video](https://github.com/louisedesadeleer/cut-video). MIT.

  ```bash
  git clone https://github.com/louisedesadeleer/cut-video.git ~/.claude/skills/cut-video
  ```

  Run with `/cut-video`. Needs ffmpeg (libx264) and `openai-whisper`; installs Montreal
  Forced Aligner on first run (through Homebrew and conda) for exact word timing.
