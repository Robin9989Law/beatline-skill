# Intake — 从一个 idea 建模型

The user will often give one sentence. That is enough. Treat it as a
**slot-filling problem**, not a conversation.

## Slots to fill (8)

| Slot | How to get it | If missing |
|---|---|---|
| 类型包 | 重生/再来 → rebirth-revenge；扮猪/战神/隐藏实力 → hidden-master；甜宠/霸总/宠滯 → sweet-ceo | default rebirth-revenge |
| 主题承诺 | 卖什么缺口：打脸 / 身份 / 宠滯 / 智斗 | pack default |
| 主角伤口 Wound | 被谁、做了什么 | pack default |
| 主角欲望 Want | 这一世要讨回什么 | 从伤口取反 |
| 对手 | 亲妹/继母/前搭档/联姻对象 | pack antagonist role |
| 开场地点 | 重生回X / 订婚宴 / 军区门口 | pack location 0 |
| 信物 | 手镐、U盘、伤疤、股权、军牌 | pack token 0 |
| 变现 | 未说则 12 集、90 秒、免费 8、首卡 8 | knobs default |

Extract names if present (`《》` 作剧名；连续 2 个汉字且像人名则入角色)。否则用类型包默认名，并在「未填槽」里标「姓名为暂定」。

## Instantiation order

1. Pick pack. Mix weights sum to 1. Secondary types only shift the currency basket, they do not swap the legal table.
2. Cast required roles from the pack. Overlay extracted names/wounds.
3. Mint secrets from pack templates, bound to these people. Every secret gets `earliestEp` / `latestEp` / holder / knownBy.
4. Mint tokens that can appear on camera. At least one token must be the evidence of the opening crime or promise.
5. Mint 3–5 locations. Episode 1 must reuse location 0. New locations are a budget, not a decoration.
6. Set audience start: `Hunger` high enough to hook, `TrustShow` medium, `Fatigue` 0, `Align` on the lead.
7. Info deck: each secret becomes 1–3 facts (plant / half / reveal). Facts are propositions, not sentences.
8. Visual limits from knobs: `max_cast_on_screen=2`, `ep_seconds`, `dialogue_cps`.

## What "构建模型" means

A model is complete when:

- Every named person has the accounts \(P, Face, M, Leverage, Mask, True, Want, Wound, Line, Express, LookSlot, Voice\)
- Every pair that will share a frame has \(Trust, Desire, Debt, Hostility, Fear, InfoGap\)
- ≥3 secrets with due dates
- ≥2 tokens
- Paywall: `free_window` and `first_gate` set, first gate on the **main debt**
- Episode 1 has 5–8 `BeatTicket`s whose `causal_support` edges exist

Stop there. Do not narrate the season.

## Tiny extractor cheats (when no LLM)

```
重生回(.{1,8})        → location_0
被(.{1,8}?)(推|害|杀|弃|骗|替) → antagonist + wound
假千金|真千金|替身     → identity secret
手镐|U盘|鉴定|军牌|股权 → token
订婚|宴会|婚礼         → opener at banquet, love interest exists
```

## Do not interview

Ask at most **one** question, and only if you cannot tell whether this is 重生, 扮猪, or 甜宠. Otherwise assume and mark.
