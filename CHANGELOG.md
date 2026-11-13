# 变更记录

## 2026-11-13 · 1.0.0 首次发布

- 按问题域从 `agent-skills` 拆出 Skill 工程主题仓，收纳 3 个 Skill：`skill-writer`、`self-evolution`（首批已发布）+ `skill-detector`（本批新增）。
- 新增 `skill-detector`：结构检查 / 8 维打分 / 红队测试 / 多模型交叉验证 / 自主改进循环。
- **权属核验**：逐行比对确认 `skill-detector` 有 4 个文件逐行来自 `sunxingboo/skill-evaluator`（MIT），原 LICENSE 原样保留；与无许可证的 `lanyasheng/skill-evaluator` 最高仅 5 行通用测试用例重合，无成段复制。新增 `ATTRIBUTION.md` 记录全部数据。
- 修正 `skill-detector/README.md` 的「个人自研」表述为「基于 MIT 上游整合改编」。
- 3 份 `README.md` 由模板骨架重写为「问题 / 用法 / 依赖 / 与其他 Skill 配合」结构。
- 新增 `scripts/check-before-push.py`（白名单 3 项 + 上游署名与免责存在性检查）。
