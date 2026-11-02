# Pacing and voice

## Reading time

- Hold any text at least **0.5 s + 0.3 s per word** after it has fully appeared.
- Commands and install lines: type at a readable speed (≈ 25 characters per second), then
  hold 1.5–2 s before the camera moves. People copy these; give them time.
- Each step of a walkthrough gets its own voice line and 5–10 s on screen.

## Rhythm

- Something changes every 5–8 s: a camera move, a cut, a card, a UI change.
- No still frame longer than ~1 s while nothing is said.
- No gap longer than ~0.6 s between voice lines; no camera hold after the action is over.
  If the film feels slow, shorten gaps across picture, voice, effects and subtitles together.
- Slow down for the part that matters most (the main how-to), speed up for the overview.

## Voice

| Voice (Kokoro, free) | Character | Good for |
|---|---|---|
| `am_puck` | energetic US male | demos, launches |
| `af_heart` | warm US female | onboarding, how-to |
| `bm_fable` | calm British male | explainers |
| `bf_emma` | clear British female | tutorials |

Paid: HeyGen (word timestamps included), ElevenLabs. Both need an account and a key.

Workflow:

1. Voice the same hook line in 2–3 voices; send the files; wait for the choice.
2. Speed 1.05 for a lively read. One file per script line, so a line can be re-recorded and
   re-timed alone.
3. Mix the lines into one narration track with fixed offsets; transcribe it
   (`npx hyperframes transcribe`) and place every action at word time + 0.2 s.
4. After any re-record: rebuild the narration, re-transcribe, re-time that scene.

Cost of time on a laptop: ≈ 5 s per line, ≈ 1 min for a 2-minute script.
