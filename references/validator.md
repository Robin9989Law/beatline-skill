# Validator

Run after compile, after re-solve, after write. Failures are production
bugs, not style notes.

| Check | Fail if |
|---|---|
| leak | A line or `must_show` makes audience know a fact before its reveal op |
| due | Secret `latestEp` passed with no reveal |
| early | Secret revealed before `earliestEp` |
| empty_pay | `true_pay` with all deltas ≈ 0 |
| fatigue | Two adjacent same `function`, or three eps same main currency |
| visual | `cast_on_screen.length` > max, unknown location, unshootable verb |
| continuity | LookSlot / wound / token jumps without a budgeted change |
| gate | First-gate episode settles main debt, or post-gate does not `pay_and_plant` |
| duration | Sum of beats ≠ `ep_seconds` ± 4 |
| dialogue | Line chars exceed `dialogue_cps * duration` |
| clone | Function sequence edit distance to last m eps below threshold |
| novel | `must_show` / `action` / lines use 心想、意识到、原来、旁白, or have no visible verb |

On fail: rewrite the **offending beat**. Do not regenerate the episode
unless season-layer constraints broke.
