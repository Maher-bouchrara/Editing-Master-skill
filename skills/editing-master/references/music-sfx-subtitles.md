# Music, sound effects, subtitles and cover

## Music

| Source | Time | Notes |
|---|---|---|
| Free CC track (Openverse, Jamendo, Free Music Archive) | ≈ 1 min to find and download, a few seconds per sample cut | Recommended. CC BY needs a credit line in the README and end card. |
| Generated locally (MusicGen) | slow on CPU: several minutes per clip | Free; fine for 15–30 s beds if there is time. |
| Paid catalog (HeyGen music) | instant | Needs an account. |

- One track for the whole film, entering at a musical point (skip a quiet intro with a
  media offset), fade in 1–1.5 s and out 3 s.
- Level: music ≈ 16 % volume (about −18 dB under the voice).

**Let the user listen first.** Send a 15–20 s sample of each candidate, then a short mix
of voice + music at the planned level:

```bash
# sample from 60 s into the track
ffmpeg -ss 60 -t 18 -i track.mp3 -af "afade=t=in:d=1,afade=t=out:st=16:d=2" sample-1.mp3
# voice + music at 16 %
ffmpeg -i voice.wav -i track.mp3 -filter_complex "[1]atrim=60:75,asetpts=PTS-STARTPTS,volume=0.16[m];[0][m]amix=inputs=2:normalize=0:duration=first" mix-preview.mp3
```

## Sound effects

- Only on visible actions: click on a click, soft typing on typing, pop on something that
  appears, whoosh on fast moves and wipes, a sparkle on a success.
- Levels: clicks 0.3–0.4, pops 0.2–0.26, whooshes 0.3–0.35, typing ≈ 0.18.
- `media-use` finds free effects; keep files in `assets/sfx/`.
- Play them to the user before using them (one file with all effects in a row is enough):
  `ffmpeg -i click.mp3 -i pop.mp3 -i whoosh.mp3 -filter_complex "[0][1][2]concat=n=3:v=0:a=1" sfx-preview.mp3`

## Word and transition sounds

On one-word screens, every word can land with a short sound, and every transition can
have its own sound. Voice, word and sound hit together: that is what makes the screen
punch. **Ask the user**, never assume: sounds on the words? which kind? the same for every
word, or a different one on the key word? sounds on the transitions?

### Sounds for words (pick one family per screen)

| Sound | Feel | Fits |
|---|---|---|
| Hit / punch (short low thump) | strong, confident | hooks, claims, numbers ("3 clicks. 0 setup.") |
| Pop | light, friendly | consumer apps, playful tone |
| Typewriter key / tick | precise, techy | developer tools, step lists |
| Camera shutter / snap | quick, editorial | feature lists, "before / after" |
| Bass drop or boom | big moment | one key word only (the brand, the result) |
| Riser (0.5–1 s) into a hit | build-up | the last word of the hook, a reveal |
| None | calm | serious topics, slow explainers |

Offer a default pattern, e.g. "a pop on every word, a hit on the key word, a riser into the
brand name", and let the user change it word by word.

### Sounds for transitions

| Transition | Sound |
|---|---|
| Circle wipe (chapter, hook card) | swoosh, or a riser + hit on the card |
| Flood reveal (inside one-word screens) | the word sound above |
| Shrink into | reverse whoosh ("suck in") |
| Zoom through | whoosh into an impact on the cut |
| Whip pan | fast whoosh |
| Blur out | soft air, or nothing |

### Timing and levels

- Each sound starts on the word's entry (the same time the word appears, = its word time
  from the transcript); a riser ends exactly on its word. A transition sound peaks on the
  cut.
- Keep word sounds short (under ≈ 0.25 s) so they do not cover the next word. If beats are
  closer than ≈ 0.25 s apart, use a lighter tick, or a sound on every other word.
- Vary the pitch slightly from word to word (±2–4 %) so a row of hits does not sound
  robotic: `ffmpeg -i pop.wav -af "asetrate=44100*1.03,aresample=44100" pop-up.wav`.
- Levels: word pops and ticks 0.2–0.28, hits 0.3–0.4, the key-word boom up to 0.45,
  whooshes 0.3–0.35. The voice stays on top; lower the music under a dense one-word run.
- Never two sounds on the same frame (a word sound and a click): keep the stronger one.
- In HyperFrames, each sound is its own `<audio>` with an `id`, `class="clip"`,
  `data-start` (the word time), `data-track-index` and `data-volume`.

### Let the user hear it

Before building, send a 5–10 s demo of one one-word screen: the voiced words with the
chosen sounds on their word times, so the user hears voice and sounds together. Build it
from the voice file and the effect files:

```bash
# voice + a pop at 0.42 s and a hit at 1.10 s
ffmpeg -i hook.wav -i pop.wav -i hit.wav -filter_complex "[1]adelay=420|420,volume=0.25[a];[2]adelay=1100|1100,volume=0.35[b];[0][a][b]amix=inputs=3:normalize=0:duration=first" word-sounds-demo.mp3
```

In the script table, give each one-word screen a **sound** column (one sound per word), so
the user approves the sounds word by word with the script.

## Voice on one-word screens

On a one-word screen the voice says each word on its own, with the tone of the screen:
short, stressed, a tiny beat between words ("Paste. Mask. Send."). A flat sentence read at
normal speed under punchy words feels wrong.

- Write the line with full stops between words ("Three clicks. Zero setup.") so the voice
  stops and stresses each word. Do not voice it as one comma-separated sentence.
- For exact control, voice each word as its own file and place each at its beat; the word
  sound and the on-screen word sit on the same time.
- Match the tone to the screen: energetic and firm for a hook, warm for a promise, calm
  and slower for a serious point. Kokoro has no tone controls; pick the voice and speed
  (1.0–1.1 for punchy words) and use punctuation. Paid voices (ElevenLabs) can take a style
  or emotion setting.
- Let the user hear the voiced one-word line with its sounds (the demo above) before it
  goes in.

## Final mix

Normalise the finished file to −16 LUFS with peaks under −1 dBTP:

```bash
ffmpeg -i in.mp4 -c:v copy -af loudnorm=I=-16:TP=-1.5:LRA=11 -c:a aac -b:a 192k out.mp4
```

## Subtitles

Ask in the style step: **burned in** or **separate files** (or both). Never assume.

| | Burned in | Separate files (.srt / .vtt) |
|---|---|---|
| Visible | always, everywhere, sound off too | only where the player or platform loads them |
| Languages | one | one file per language, viewers switch |
| Change a line | edit the captions and re-render | edit the text file, re-upload |
| Best for | short social clips that autoplay muted, ads | how-tos, websites, several languages |

Rules for both:

- Cue times from the transcript (`npx hyperframes transcribe narration.wav`, ≈ 20 s for a
  4-minute film; pass `--model small --language <code>` for a non-English voice, since
  `small.en` translates into English).
- 1–2 lines per cue, ≈ 42 characters per line; a cue opens at or before its first word and
  closes at or after its last.
- Write each translation for its language; flag them for a native speaker to review.

### Separate files: export SRT and VTT

`.srt` for most players and platforms (YouTube, LinkedIn, Vimeo, desktop players), `.vtt`
for web players (`<track>` in HTML5 video). Export from the transcript, one file per
language, named `video.<lang>.srt` / `video.<lang>.vtt`:

```bash
npx hyperframes transcribe assets/transcript.json --to srt -o out/video.en.srt
npx hyperframes transcribe assets/transcript.json --to vtt -o out/video.en.vtt
```

- Read the exported file: fix wrong words, merge one-word cues, split cues over 2 lines.
- For a translation, copy the file and translate the text lines only; keep every timestamp.
- In VTT, cue settings `size:86% align:center`, no fixed line position, and a small fixed
  cue size in the player so lines never leave the frame.
- Tell the user the files are plain text and can be edited by hand.

### Burned in

Two ways. Prefer the first, because the captions then show in the preview and the user
approves them with the rest of the film.

1. **Captions as a HyperFrames layer** (see the `hyperframes` skill, `references/captions.md`,
   or a ready-made style from `npx hyperframes catalog --tag caption-style --json`):
   - One host with `data-track-kind="captions"`, one group visible at a time, 3–5 words per
     group for a voiceover.
   - Size each group with `window.__hyperframes.fitTextFontSize(text, { maxWidth })`:
     `maxWidth` 1600 for 16:9, 900 for 9:16. A full-width container with centred text; never
     `left: 50%; transform: translateX(-50%)`, which clips at the edges.
   - 80–120 px from the bottom in 16:9; about 600–700 px from the bottom in 9:16 (above the
     platform's buttons). Always inside the 80 % title-safe box.
   - Snapshot the longest cue at every scene: no word may touch or leave the frame or cover
     the UI being explained.
2. **ffmpeg on the finished file**, from the SRT (when the film is already rendered, or for
   a second burned-in version in another language):

   ```bash
   ffmpeg -i video.mp4 -vf "subtitles=video.en.srt:force_style='FontName=Inter,FontSize=16,Bold=1,PrimaryColour=&H00FFFFFF,OutlineColour=&H80000000,BorderStyle=1,Outline=2,Shadow=0,Alignment=2,MarginV=20,MarginL=30,MarginR=30'" -c:a copy video.en.burned.mp4
   ```

   - `force_style` sizes are on a 384×288 grid scaled to the video: `FontSize=16` is about
     60 px at 1080p; `MarginL/R=30` keeps lines ≈ 150 px inside the edges, so long lines
     wrap instead of leaving the frame.
   - Run it from the folder that holds the .srt (a Windows path with `C:` breaks the filter).
   - Pull frames at the longest cues and check nothing is cut off.

When both are wanted, burn in the main language and ship SRT/VTT files for every language.

## Cover

A 1920×1080 cover in the brand look: title, one-line promise, a product shot, duration.
Export two versions: with a play button (thumbnails, social) and without (poster frame).
