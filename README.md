# 拍线 Beatline

Grok skill：从一个短剧 idea **先建模型和节拍票**，再允许填词。

节拍是魂。故事只是魂的一次具体实例。  
这不是小说。每一拍必须能被镜头里 1–2 个人演出来。

## 协议

1. idea 进来 → 五层模型（季 / 人物账户 / 观众 / 信息牌 / 镜头可行性）
2. 立刻排出第 1 集 BeatTicket（5–8 拍）。不要写故事。
3. 对白只是表演层：不能改在场的人、不能揭未授权的牌、不能把两拍揉成散文。
4. 换类型 / 时长 / 卡点，只拧旋钮和类型包，不重写提示词。

## 安装

```bash
git clone https://github.com/Robin9989Law/beatline-skill.git beatline
# 放到 .grok/skills/beatline/
```

触发词：短剧、竖剧、剧本、分镜、节拍、卡点、重生复仇、战神扮猪、甜宠、BeatTicket。

## 目录

```
SKILL.md                 路由与硬约束
references/intake.md     idea → 模型
references/beat-ticket.md  最小商品单元
references/on-camera.md    必须可演，禁止内心戏
references/primitives.md   18 个功能原语
references/solver.md       分层搜
references/writer-contract.md  表演权，没有创作权
references/validator.md    穿帮即失败
packs/                   重生复仇 / 战神扮猪 / 霸总甜宠
```
