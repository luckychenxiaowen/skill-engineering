# ONBOARDING

> 新贡献者路径；细则见 [CONTRIBUTING.md](../CONTRIBUTING.md)，发布门槛见 [PUBLISH.md](../PUBLISH.md)。

## 1. 这个仓库在做什么

Skill 工程主题仓：把「写 Skill → 评 Skill → 复盘迭代」串成可复跑流程，让 Skill 从一次性草稿变成可维护资产。只收 Skill 生命周期（写 / 评 / 迭代）上的工具；每个 `skills/<name>/` 目录独立可用，复制到 Agent 的 `skills/` 即生效。

## 2. 目录结构与三个 Skill 的职责

```text
skills/skill-writer/   写：素材 → 规范 Skill（frontmatter / 触发词 / 执行引导）
skills/skill-detector/ 评：结构检查 + 8 维打分 + 红队 + 多模型验证 + 改进循环
skills/self-evolution/ 迭代：五步复盘（品味过滤 → 蒸馏 → Memory → Skill → Eval）
scripts/check-before-push.py   提交前硬门槛校验；ATTRIBUTION / PUBLISH / CONTRIBUTING / CHANGELOG 为权属与规范
```

- `skill-writer`：把 AI/人工初稿改写成可落地的 Skill 文本；不是普通润色工具。
- `skill-detector`：**基于 MIT 上游整合改编，并非纯自研**，4 个文件逐行来自 `sunxingboo/skill-evaluator`，上游 LICENSE 原样保留。
- `self-evolution`：外部信息走五步闭环，决定进 Memory、固化成 Skill 还是淘汰。

推荐顺序：`skill-writer` → `skill-detector` 快速模式 → 真实用一次 → `self-evolution` 复盘 → 深挖再跑深度/改进模式。

## 3. 新增一个 Skill 的步骤

1. 先过问题域：必须落在 Skill 生命周期上，否则不入本仓。
2. 建 `skills/<name>/SKILL.md` + `README.md`；需要模板加 `references/`，需要脚本加 `scripts/`。
3. README 写清「解决什么问题 / 怎么用 / 依赖与凭据 / 与其他 Skill 如何配合」，禁止「(见 SKILL.md)」。
4. 第三方代码必须留痕：`ATTRIBUTION.md` 登记来源、许可证、逐文件关系，目录内原样保留上游 LICENSE；无许可证上游只可参考思路。
5. 凭据外置：只从环境变量或已 gitignore 的本地配置读取，仓内只放占位符。
6. 改 `scripts/check-before-push.py` 的 `ALLOWED_SKILLS`，同步 `README.md` 清单与 `CHANGELOG.md`。
7. 跑 `python scripts/check-before-push.py`，全项 PASS 才提交。

## 4. 提交前检查清单

- [ ] `python scripts/check-before-push.py` 全项 PASS（文件齐全 / 白名单精确 3 项 / 各 Skill 有 SKILL.md 与 README.md / README 非模板）。
- [ ] 权属门槛：`skills/skill-detector/LICENSE` 在且 `Copyright (c) 2026 sunxingboo` 未改；`ATTRIBUTION.md` 结论成立；`skill-detector/README.md` 不称「纯自研」。
- [ ] 无真实凭据 / AppID / 私钥 / 内网 IP / 本机绝对路径 / 雇主相关词 / 凭据文件。
- [ ] README 与 CHANGELOG 已同步；许可证变更、权属争议、检查 FAIL 任一出现即暂停。
