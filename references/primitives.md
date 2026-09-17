# 18 primitives

Functions are legal moves, not labels. The same primitive has different
legal \(\Delta\) inside each genre pack.

| id | 名 | Default job |
|---|---|---|
| cold_hook | 冷开钩 | Image before name. No explanation. |
| rehook | 回钩 | Turn the previous episode into a new conflict, not a recap. |
| press | 加压 | Raise Hunger or Debt without paying. |
| fake_good | 假好 | Comfort that is a trap. |
| fake_win | 假胜 | Lead looks up; next beat takes it back. |
| true_pay | 真爆 | Spend Hunger, move the pack's main currency. |
| backlash | 反噬 | Payoff costs the lead Face or M. |
| identity_half | 身份半露 | Show Mask ≠ True without naming True. |
| evidence_show | 证物出示 | Token on camera. Fact becomes visible_on_screen. |
| relation_flip | 关系翻转 | One \(R_{ij}\) axis changes sign or jumps ≥0.3. |
| third_enter | 第三方进场 | New body, then immediately two-shot. |
| flashback | 时空闪回 | Own location asset. One ticket only. |
| rule_reveal | 规则揭示 | System / house rule, one sentence max. |
| resource_settle | 资源结算 | M or Leverage integer change. |
| public_punish | 公开处刑 | Face hit with witnesses. Sweet pack down-weights this. |
| private_deal | 私下交易 | Two-shot, InfoGap trade. |
| cut | 切断 | End on unfinished action / half reaction / new card. |
| pay_and_plant | 兑现旧债同时种新债 | Mandatory on the episode after a gate. |

## Episode recipes (starting points, not prisons)

- **Opener (ep 1):** cold_hook → rehook → press → evidence_show → fake_good → true_pay → pay_and_plant → cut
- **Press:** rehook → press → private_deal → press → identity_half → cut
- **Bait (gate-1):** press → fake_win → backlash → evidence_show → cut
- **Gate:** rehook → true_pay → press → cut (Hunger and main debt still open)
- **Post-gate:** pay_and_plant → relation_flip → press → cut
- **Finale-1:** evidence_show → public_punish or relation_flip → true_pay → cut
- **Finale:** true_pay → resource_settle → (optional backlash) — only here may Hunger go near 0

`pay_per_ep` caps `true_pay` + `public_punish`. Extra intensity goes to press / plant.

## Anti-clone

No two adjacent tickets share `function`. No three consecutive episodes share the same main `payoff_currency`. Repeat **motifs** (the same bracelet, the same line of dialogue reversed), never plots.
