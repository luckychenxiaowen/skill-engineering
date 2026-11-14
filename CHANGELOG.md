# 变更记录

## 2026-11-14 · 1.1.0 补齐三份 SKILL.md

- `skill-writer/SKILL.md`：原文件是一份与本仓职责无关的长文（「人类作家」反检测工具说明，484 行），与 `README.md`、仓根 `README.md`、`docs/ONBOARDING.md` 声明的「把素材写成 Skill」不符，也没有 frontmatter 规范、触发词、判据与渐进式披露。按声明职责重写为技能撰写流程（v1.0.0）：五步流程 + SKILL.md 模板 + 触发词规则 + Gotchas + 与下游交接；同步修正 `README.md` 中按旧内容写的用法与边界。
- `skill-detector/SKILL.md`：修正非法 `name`（`skill检测` → `skill-detector`），补「什么时候不用」「输入确认」「输出与验收」「执行约束」「Gotchas」「边界与免责」「资源与渐进式披露」「与本仓其他 Skill 的交接」。
- `self-evolution/SKILL.md`：补「什么时候不用」「输入与产出」「完整示例」「边界」与交接表；把只对作者本机成立的表述（IMA 笔记、感知脑、带日期的固化记录）泛化为可选模块；修正「五篇文章 / 五种失败模式」与实际条目数不符；明确 L2 交叉验证与每周固化都是可选模块。
- 三份 `SKILL.md` 的 frontmatter 统一为 `name` + `description`（含 TRIGGER / DO NOT TRIGGER）+ `version`。

## 2026-11-13 · 1.0.0 首次发布

- 按问题域从 `agent-skills` 拆出 Skill 工程主题仓，收纳 3 个 Skill：`skill-writer`、`self-evolution`（首批已发布）+ `skill-detector`（本批新增）。
- 新增 `skill-detector`：结构检查 / 8 维打分 / 红队测试 / 多模型交叉验证 / 自主改进循环。
- **权属核验**：逐行比对确认 `skill-detector` 有 4 个文件逐行来自 `sunxingboo/skill-evaluator`（MIT），原 LICENSE 原样保留；与无许可证的 `lanyasheng/skill-evaluator` 最高仅 5 行通用测试用例重合，无成段复制。新增 `ATTRIBUTION.md` 记录全部数据。
- 修正 `skill-detector/README.md` 的「个人自研」表述为「基于 MIT 上游整合改编」。
- 3 份 `README.md` 由模板骨架重写为「问题 / 用法 / 依赖 / 与其他 Skill 配合」结构。
- 新增 `scripts/check-before-push.py`（白名单 3 项 + 上游署名与免责存在性检查）。
