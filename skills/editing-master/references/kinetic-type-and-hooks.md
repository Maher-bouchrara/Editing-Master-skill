# Kinetic type and hooks

Kinetic type is text that moves to the voice. Use it for the hook, chapter changes and
attention resets, not on every scene. Working code: `starter/compositions/hook.html` and
`starter/compositions/chapter.html`.

## The hook (first 5 seconds)

Pick one pattern and say it in one sentence:

| Pattern | Example |
|---|---|
| Problem → promise | "Every day, teams paste customer data into AI chatbots. Once it's sent, it's gone." |
| Surprising claim | "This video wasn't filmed or edited. It was written in code." |
| Question | "What if your secrets never left your browser?" |
| Result first | Show the finished outcome for 2 s, then "Here's how." |

Then the brand reveal (2–3 s), then numbered steps.

## One-word screens (flood screens)

- Full-bleed brand colour, one or two words per beat, centred, 160–200 px, weight 900,
  tight letter spacing (−0.05em).
- Each beat enters on its spoken word: blur 10 px → 0 and scale 1.18 → 1 in ~0.16 s
  (`power4.out`); it leaves 0.04 s before the next word (~0.08 s).
- Swap the flood colour (brand ↔ dark) on a key word to mark a turn in the sentence.
- Last word exits into the next scene (shrink + blur), not a plain fade.
- One accent word in the brand colour per screen, at most.

## Word-by-word lines

For a sentence that must be read, reveal words ~0.1 s apart (blur-in), keep the line on
screen until it is read (see pacing), then clear it in one move.

## Chapter cards

A circle wipe in brand colour opens a card: a pill label ("THE MAIN PART", "STEP 2"), a big
title (110–130 px) and a short line. Hold 3–4 s, then wipe out to the next scene. Use one
for each big part of the video, especially the part people must not miss.

## Attention resets (every 20–30 s)

- A hook card: "WOW · The easiest part" before the simplest step.
- A pattern break: "You see all this? There's an even simpler way." on a dimmed full-screen
  card, then zoom back into the UI.
- A number: "3 clicks. 0 setup." as two flood screens.

## Script rules

- One idea per scene, 15–20 spoken words, plain words, active voice.
- Show, don't list: every sentence has an on-screen action that proves it.
- Numbered steps ("Step 1 · Open …") with a short step chip that appears, then leaves.
- Close on one line that sums up the value, then the logo.
