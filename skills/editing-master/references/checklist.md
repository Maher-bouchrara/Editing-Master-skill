# Checklist: what went wrong without each rule

Each rule below came from a real fix while making product videos with this workflow.

| Rule | What happened without it |
|---|---|
| Ask voice, presenter, music, clicks, zooms first | Rework after the first cut |
| Voice samples by ear | Voice names say little; one listen decides |
| Rebuild real UI from source, do not invent | A menu with a non-existent "Add model" had to be redone |
| Ask for a screenshot when the look is unsure | Colours and corner radius looked off from the real popup |
| Sync from the transcript | Highlights ran one item ahead of the words |
| One click = one state change | A switch flipped off and on for a single click |
| Readable holds on commands | Viewers could not read the install steps before the camera moved |
| A hook card before the easiest step | The simplest way was missed because it came last and fast |
| The main how-to as its own chapter | The most important part was squeezed at the end |
| No gaps > 0.6 s | The cut felt slow; 10 s of dead air were removed |
| Approval before render | Renders take minutes; the preview is where changes happen |
| Fixed subtitle size, no fixed line | Two-line subtitles ran out of the frame |
| No hardware specs or private details on screen | They had to be removed after review |

## Before you send the preview

- [ ] `npx hyperframes check` passes with 0 errors.
- [ ] Snapshots at every step and every cut look right.
- [ ] Every action is on its word.
- [ ] Every text holds long enough to read.
- [ ] No more than ~0.6 s of silence between lines.
- [ ] 3–5 transition kinds, each with a cause.
- [ ] Music under the voice; effects only on visible actions.
- [ ] Subtitles in the form the user chose (burned in or SRT/VTT files); the longest cue
      stays inside the frame.
