# Transitions and camera

Working code: `starter/compositions/ui-focus.html` (focus camera, cursor, click, step chip)
and the scene exits in `starter/compositions/*.html`.

## Camera: the focus helper

Wrap everything the camera sees in one element (`#cam`) with `transform-origin: 0 0`, and
move it with:

```js
// Put point (cx, cy) of the 1920×1080 stage at the screen centre, scaled by s.
const focus = (cx, cy, s) => ({ x: 960 - cx * s, y: 540 - cy * s, scale: s });
tl.to("#cam", { ...focus(1390, 380, 1.75), duration: 0.9, ease: "power3.inOut" }, t);
```

Grammar:

1. Push in on the exact control the voice names (1.3–2.3×), 0.7–0.9 s, `power3.inOut`.
2. Hold while it acts, then **1.5 s more** so it can be read.
3. Pull back to wide (`x:0, y:0, scale:1`) when the voice moves on.
4. Never move the camera while text the viewer must read is being typed.
5. Slow pans across lists while items are named.
6. Elements GSAP animates must not have a CSS `transform` of their own.

## Cursor and clicks

- The cursor moves with intent (0.5–0.8 s, `power2.inOut`), arrives ~0.15 s before the
  spoken word, and clicks on the word.
- Click = cursor scale 0.85 for 0.1 s + a ripple ring + a click sound.
- One click = one state change. Highlight boxes keep a little padding around icons and text.

## Transitions: one main style, one or two accents

| Transition | How | Use it for |
|---|---|---|
| Circle wipe | `clipPath: circle(0% → 80%)` on a brand-colour layer | chapter cards, hook cards |
| Flood reveal | flood colour swaps behind words | inside one-word screens |
| Shrink into | last element scales to ~0.2 and blurs into the next scene | hook → first UI scene |
| Zoom through | camera pushes into a button until it fills the frame, cut on the click | "click → new screen" |
| Blur out | `opacity 0` + `blur(8px)` in 0.25 s | quiet scene ends |
| Whip pan | stage `x: 0 → −300` + motion blur in 0.25 s, next scene enters from the right | fast changes of topic |

Rules: every transition has a cause (a click, a new chapter, a new topic). Use 3–5 kinds in
a film, never the same fade on every cut.

Each transition can have its own sound (swoosh on a circle wipe, reverse whoosh on shrink
into, whoosh + impact on zoom through, fast whoosh on a whip pan, little or nothing on a
blur out). Ask the user whether they want transition sounds, and play them first; the
sound peaks on the cut. See `music-sfx-subtitles.md`, "Word and transition sounds".

## Scene structure (HyperFrames)

- Each scene is a sub-composition in `compositions/` with a paused GSAP timeline registered
  as `window.__timelines["<id>"]`, mounted in `index.html` with `data-start`/`data-duration`.
- Keep a wrapper inside each scene as the only timed element (`class="clip"`); do not put a
  timed `<video>` inside another timed element.
- Hide things with CSS `opacity: 0`, not with `tl.set` at time 0.
