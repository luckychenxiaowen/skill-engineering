# skill-writer · 把内容写成 Skill

解决**「有一段素材，怎么落成一份 Agent 能正确加载的 Skill」**：补 frontmatter、写清触发与排除条件、把散乱经验整理成可执行流程与判据，并按渐进式披露拆分 `references/` 与 `scripts/`。

## 什么时候用它

- 有一篇方法论文章 / 一套踩坑笔记，想变成可复用 Skill
- 已有 `SKILL.md` 但触发词含糊，Agent 经常不加载或误加载
- 需要批量产出多个 Skill，且要保证术语与格式一致

## 怎么用

1. 整目录复制进你的 Agent 的 `skills/` 目录
2. 把素材交给 Agent，说「用 skill-writer 把这个写成 Skill」
3. 检查产出的 `SKILL.md` frontmatter（`name` / `description` / 触发词）是否覆盖你的真实使用场景

`SKILL.md` 里定义了五步流程（定问题域 → 把素材拆成触发/步骤/判据/反例 → 起草 → frontmatter 与触发词自查 → 渐进式披露与交付），并给出 SKILL.md 模板、触发词设计规则与常见反例。**零外部依赖**，不需要任何 API、脚本或凭据。

## 与本仓其他 Skill 怎么配合

| 顺序 | 用什么 | 得到什么 |
|---|---|---|
| 1 | **本 Skill** | 一份结构合规的 `SKILL.md` |
| 2 | `skill-detector` 快速模式 | 8 维打分 + 结构检查 + 改进建议 |
| 3 | 真实用一次 | 实际触发与效果记录 |
| 4 | `self-evolution` | 复盘：改 / 留 / 写入长期记忆 |

## 边界

- 产出的是**文档级 Skill**，不是运行时框架；不含脚本执行环境。
- 不替你决定某个 Skill 该不该存在，也不负责把它部署到你所用 Agent 的运行时；触发词能否命中由该 Agent 的加载器决定。
- 素材不足以支撑判据时，明说"待确认"，不补想象。
- 不接收真实凭据、真实 AppID 或雇主相关语境作为输入素材。

## 来源与文件

个人自研，无第三方代码。本目录含 `SKILL.md`。仓根 [ATTRIBUTION.md](../../ATTRIBUTION.md) 记录了本仓全部第三方来源（本 Skill 无）。
