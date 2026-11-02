# Music, sound effects, subtitles and cover

## Music

| Source | Time | Notes |
|---|---|---|
| Free CC track (Openverse, Jamendo, Free Music Archive) | ≈ 1 min | Recommended. CC BY needs a credit line in the README and end card. |
| Generated locally (MusicGen) | slow on CPU | Free; fine for 15–30 s beds if there is time. |
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

## Final mix

Normalise the finished file to −16 LUFS with peaks under −1 dBTP:

```bash
ffmpeg -i in.mp4 -c:v copy -af loudnorm=I=-16:TP=-1.5:LRA=11 -c:a aac -b:a 192k out.mp4
```

## Subtitles

- One WebVTT file per language, cue times from the transcript, 1–2 lines per cue,
  ≈ 42 characters per line.
- Write each translation for its language; flag them for a native speaker to review.
- Cue settings `size:86% align:center`, no fixed line position, and a small fixed cue size
  in the player so lines never leave the frame.
- Ship them as separate tracks, not burned in, so they can be edited by hand.

## Cover

A 1920×1080 cover in the brand look: title, one-line promise, a product shot, duration.
Export two versions: with a play button (thumbnails, social) and without (poster frame).
