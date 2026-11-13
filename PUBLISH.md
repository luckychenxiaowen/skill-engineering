# 发布说明

本仓是 `agent-skills` 按问题域重组后的 Skill 工程主题仓，只收**同一条生命周期**上的工具：写、评、迭代。原仓仍保留首批 7 个 Skill 的快照，本仓不覆盖、不删除原仓内容。

## 检查是硬门槛

```
python scripts/check-before-push.py
```

脚本检查：必需文件齐全、Skill 白名单精确匹配（只允许 3 个）、每个 Skill 有 `SKILL.md` + `README.md`、`skill-detector` 的上游 LICENSE 与 `ATTRIBUTION.md` 声明齐全且不再自称纯自研、无私钥 / 密钥 / 真实 AppID / 内网 IP / 本机绝对路径 / 雇主特定词 / 凭据文件。

任何一项 FAIL 都不提交。

## 权属门槛（本仓特有）

`skill-detector` 含 MIT 上游的逐行复制文件，因此每次提交都必须复核：

1. `skills/skill-detector/LICENSE` 存在且 `Copyright (c) 2026 sunxingboo` 未被改动
2. `ATTRIBUTION.md` 里的来源表与逐行比对结论仍然成立
3. `skills/skill-detector/README.md` 不得写「纯自研 / 手工自研」

这三条是**停止条件**：任一不满足即暂停发布。

## 试点纪律

- **继续条件**：至少 1 次真实使用记录（一个 Skill 用 `skill-detector` 打分 → 用一次 → `self-evolution` 复盘），且每份 README 有可复跑示例
- **停止条件**：上游许可证变更 / 出现权属争议 / 检查脚本任一 FAIL / 引入需要凭据才能跑的依赖 / 无法用一句话讲清本仓问题域

停止条件缺失不得开工。
