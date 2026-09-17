# Solver — 分层搜，不要重模型

State is discrete and constraints are many. Search in layers.

## Season layer

Enumerate (small):

- Secret due dates inside `[earliestEp, latestEp]`
- `first_gate` on the main debt, not a side plot
- Lead \(P\) staircase according to `power_slope`
- Per-episode main currency from the basket, with `switch_cost`

Emit a rail of N episodes: `{ role, currency, secret_ops[], gate }`

## Episode layer

Short horizon, 5–8 beats, on the pack's legal action table.
Score (do not maximize stimulation — schedule inventory):

- Completes hook in `hook_sec`
- Pulse every `pulse_sec`
- Ends at `cut_hunger`
- Does not leak
- Reuses locations / LookSlot
- Respects `pay_per_ep`
- `clone_distance` vs last m episodes' function sequence

## Beat layer

Fill `must_show / must_not / shot_grammar / cast / location`.
If visually infeasible, **downgrade the action, not the function**.
Five-person banquet slap → two people outside the door, banquet as sound.

## Write layer

LLM fills lines and shootable description only.

## Write-back

Parse lines against the info deck. If a sentence makes `known_by.audience`
true for a fact not revealed this beat, rewrite that beat.

## Gate constraints (hard)

- End of free window: Hunger and unsolved main debt above threshold
- First card cuts on unfinished main debt
- Episode after card: pay a small old debt, plant a larger new one
- Same suspense is never used as a card twice
