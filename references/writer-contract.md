# Writer contract — 故事是实例，不是作者

The tickets are the soul. What you write is **one embodiment**.
Another take on the same tickets is a different story and the same show.

The writer (human or LLM) receives BeatTickets and the on-screen cast's
`Voice`. It returns `lines` and `action` per ticket.

## Stance

- Do not merge beats into a flowing scene "so it reads better". Flow is how
  the soul goes flat.
- Keep ticket boundaries visible in the page (blank line / shot cut).
- If a nice sentence needs a new plot move, **mint a beat** — do not sneak
  the move into prose.

## Allowed

- Wording, pause, breath, a look
- Blocking **inside** the shot grammar
- Token handling described in `must_show`
- Cutting on the prescribed `cut_type`

## Forbidden (reject the take)

- Adding or removing a person on screen
- Flipping a fact not listed in `info_ops`
- Resolving Hunger / main debt on a non-finale ticket
- Changing location
- Voice-over that names a secret
- Homogenized diction (all characters one mouth). Check `Voice`.
- Recap paragraphs, scene essays, "这一集讲了…"

## On camera (hard)

This is performance for a lens, not fiction for a reader.
`action` must be a body + a shootable verb + optional token.
No 心想 / 意识到 / 感到 / 原来 / 旁白.
Emotion = a face, a hand, a withheld line. See [on-camera.md](on-camera.md).

```
chars ≤ dialogue_cps * (t_end - t_start)
lines ≤ dialogue_budget.lines
```

Vertical drama prefers one short line plus a look. If the ticket is
`prop_insert` or `reaction`, 0–1 lines.

## Output

For each ticket, keep the JSON and add:

```json
{
  "action": "沈昭抬手，把沈晚的镐子转过 90 度，刮痕正对吊灯。",
  "lines": [{ "who": "沈昭", "text": "这道痕，哪来的？" }]
}
```

No scene headings, no recap, no parenthetical emotion essays.
`emotion_tag` is for performance/voice, not for the narrator.

If asked for a "剧本", still walk ticket by ticket. The page is an instance
of the soul, not a replacement for it.
