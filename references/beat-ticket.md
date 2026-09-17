# BeatTicket — 最小商品单元

One beat = one state transfer + one shootable instruction.
Downstream cuts 3–8s per shot; payoff shots may be 2–3s.

The writer LLM is allowed to see tickets, never the "vibe".

```text
beat_id, ep, t_start, t_end
function            # see primitives.md
channels            # which accounts move: P, Face, M, Leverage, R_ij, I
delta               # signed, bounded
info_ops            # plant | hide | half | reveal + fact_id
payoff_currency     # face_slap | sweet | angst | burn | wit | identity
intensity           # 0–1, limited by fatigue + budget
must_show           # on-camera action or prop (required)
must_not            # no explaining, no reveal, no location change
cast_on_screen      # asset ids, ≤ max_cast_on_screen
location_id
shot_grammar        # 正反打 | 单人推进 | 物特写 | 反应切
dialogue_budget     # lines, chars per line
cut_type            # 停在动作未完成 | 停在反应一半 | 停在新牌进场
causal_support      # event-graph edge id; no edge → do not emit
```

## Fill rules

- `must_show` is concrete: a person, a verb from the shootable list, a token. Not "气氛更紧张".
- `must_not` always blocks narrator leak of any fact not in this beat's `info_ops`.
- `cast_on_screen` length 1 or 2. A third person is a reaction insert in the next ticket, not a crowd.
- `dialogue_budget.chars_per_line` ≤ `dialogue_cps * shot_seconds`.
- `cut_type` on the last beat of a free episode before the gate must be `action_unfinished` or `new_card`, never a settlement.

## JSON shape (writer-facing)

```json
{
  "beat_id": "e01b03",
  "ep": 1,
  "t_start": 18,
  "t_end": 28,
  "function": "evidence_show",
  "channels": ["I", "Face"],
  "delta": { "Face:沈晚": -0.08, "InfoGap:沈昭→沈晚": -0.1 },
  "info_ops": [{ "op": "half", "fact_id": "f_bracelet_scratch" }],
  "payoff_currency": "identity",
  "intensity": 0.62,
  "must_show": "红宝石手镐内壁的刮痕转到灯光下",
  "must_not": "不得说出推崖或亲子鉴定",
  "cast_on_screen": ["沈昭", "沈晚"],
  "location_id": "loc_banquet",
  "shot_grammar": "prop_insert",
  "dialogue_budget": { "lines": 1, "chars_per_line": 12 },
  "cut_type": "reaction_half",
  "causal_support": "edge_scratch_from_push"
}
```
