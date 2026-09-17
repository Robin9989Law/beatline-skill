---
name: beatline
description: >
  Compile a short-drama (竖屏短剧) idea into a production model and beat tickets
  before any prose is written. Use when the user pitches a series idea, wants
  a 短剧/竖剧/剧本/分镜, asks for 节拍/卡点/打脸/重生/战神/甜宠 structure, or
  needs a BeatTicket JSON contract for a writer LLM or shot generator.
  Triggers on 短剧, 竖剧, 剧本, 分镜, 节拍, 卡点, 大纲, idea, logline,
  重生复仇, 战神扮猪, 甜宠, BeatSpec, BeatTicket.
---

# 拍线 Beatline — 节拍是魂，故事是实例

Once you write the story first, structure flattens. **Beats come first.
They are the inner soul. Story is only one concrete instance of that soul.**

This is **not a novel**. Every beat must be playable by people in a vertical
frame. Interiority that cannot be acted is illegal. If the camera cannot
see it on a body or a token, it is not a beat.

Do not write a story first. An idea is a request to instantiate state and
schedule beats. Dialogue is a later, optional performance pass — replaceable
without touching the soul.

Core rule: **parameters live on state, inventory, and legal transitions.
The prose layer has performance rights only, never authorship of plot.**

If a sentence cannot be traced to a BeatTicket function + delta + info_op,
**and cannot be acted on camera**, it is not the show. Cut it or mint a
visible beat for it.

## Protocol (every invocation)

### 1. Load only what you need

- Always: this file.
- Instantiating from an idea: [references/intake.md](references/intake.md)
- Emitting tickets: [references/beat-ticket.md](references/beat-ticket.md) **and** [references/on-camera.md](references/on-camera.md)
- Picking functions: [references/primitives.md](references/primitives.md)
- Season / episode search: [references/solver.md](references/solver.md)
- After tickets, if asked to write lines: [references/writer-contract.md](references/writer-contract.md)
- Checks: [references/validator.md](references/validator.md)
- Genre legal tables: `packs/<id>.md` (rebirth-revenge / hidden-master / sweet-ceo)

Do not load every pack. Detect one primary pack; others may mix as weights.

### 2. Detect the job

| User says | Job |
|---|---|
| idea / logline / 一句话 / 设定 | `compile` — model + season rail + ep1 tickets |
| 第N集 / 展开节拍 | `beats` — tickets for that episode |
| 对白 / 写成剧本 / 故事 | `write` — **instance** the soul; tickets frozen |
| 校验 / 会不会穿帮 | `validate` |
| 换类型 / 换时长 / 换卡点 | `re-solve` — same bible, new knobs |

Default job is `compile`. Never skip it and jump to prose.
`write` is embodiment, not invention. Another writer (or another take)
can instance the same tickets into a different story. The soul does not move.

### 3. Compile (the hard step)

Follow [references/intake.md](references/intake.md). From one idea, fill:

1. Genre mix + theme promise (what gap this show sells)
2. Five state layers: season bible \(W\), characters \(C_i\), audience \(A\), info deck \(I\), visual limits \(V\)
3. Producer knobs (do not invent a new prompt; slide numbers)
4. Secret schedule + first-gate + per-episode currency
5. **Episode 1 BeatTickets immediately** (5–8 tickets). Other episodes: role + currency + secret ops, expand on demand

Output order is fixed:

```text
1. 立项卡（类型、承诺、旋钮）
2. 人物与关系账户
3. 秘密库 / 代币库 / 场景资产
4. 12集轨道（卡点、主货币、秘密 due）
5. 第1集 BeatTicket JSON   ← 这是魂，停在这里
6. 未填槽（最多 3 条，不要盘问）
```

Do not append a "第一集故事". If the user wants instance, they ask for `write`.

If the idea is enough to cast a lead, an antagonist, a wound, and a first location, **do not ask questions**. Invent the minimum missing names and mark them as assumed.

### 4. What you must not do

- Do not write a synopsis, episode recap, or "第一集故事" as the deliverable of `compile`.
- Do not let a narrator explain a secret the audience should not know yet.
- Do not put more people on screen than `max_cast_on_screen` (default 2 for 竖屏对峒).
- Do not reveal a secret before `earliestEp`, or miss `latestEp`.
- Do not cut the first paywall on a side-plot settlement.
- Do not change who is present, which card flips, or whether the episode resolves, when writing dialogue.
- Do not write novel interiority (`心想/意识到/原来`). Load [references/on-camera.md](references/on-camera.md). If it cannot be performed, it is not a beat.

### 5. Writer pass (only when asked)

Load [references/writer-contract.md](references/writer-contract.md). For each ticket, fill `lines` + `action` inside the budgets. Then run the validator. On leak: rewrite **that beat**, not the episode.

The story that comes out is **one take**. Same tickets can instance again.

## Flexibility

Swap type / duration / monetization by changing knobs + the legal table, not by rewriting instructions. Same soul engine, different pack, different instance.
