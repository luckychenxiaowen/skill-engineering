# skill-engineering

把「写一个 Skill → 评一个 Skill → 复盘迭代」串成一套可复跑的工程方法，让 Skill 从一次性草稿变成可维护的资产。

本仓收 **3 个 Skill**，覆盖 Skill 的生命周期：写、评、迭代。每个目录独立可用，复制进你的 Agent 的 `skills/` 目录即可。

## 这个仓解决哪一类问题

Skill 写完就放着，过两周自己都看不懂当初为什么这么写；改一版不知道是变好还是变坏；多个 Skill 之间也没法横向比。本仓给的是三件配套工具：**规范化产出 → 结构化打分与红队 → 带评分的使用复盘**。

## 3 个 Skill 怎么配合

| 阶段 | Skill | 干什么 | 什么时候用 |
|---|---|---|---|
| 写 | [skill-writer](skills/skill-writer) | 把一段内容重写成符合 Skill 规范的格式（frontmatter / 触发词 / 执行引导） | 有素材、要落成 Skill 时 |
| 评 | [skill-detector](skills/skill-detector) | 结构检查 + 8 维打分 + 红队测试 + 多模型交叉验证 + 自主改进循环 | 发布前审计、两个 Skill 横向对比、找短板 |
| 迭代 | [self-evolution](skills/self-evolution) | 五步闭环复盘：五维评分 → 处理决策 → 可信度标注 → 写入长期记忆 / 临时验证区 | 用过一次之后，决定改还是留 |

推荐顺序：`skill-writer` 产出 → `skill-detector` 快速模式打分 → 真实使用一次 → `self-evolution` 复盘 → 需要深挖时再跑 `skill-detector` 深度/改进模式。

## 用法

1. 进 `skills/<name>/`，读 `SKILL.md` 的 frontmatter
2. 整个目录复制到你的 Agent 的 `skills/` 目录
3. `skill-detector` 的深度模式可选接百度千帆 API（见其 `README.md`）；**默认策略 C 串行多视角，零外部依赖、不需要 Token**

## 第三方来源（重要）

`skill-writer` 与 `self-evolution` 为个人自研、无第三方代码。

`skill-detector` **不是纯自研**：其中 4 个文件逐行来自 `sunxingboo/skill-evaluator`（MIT），原 LICENSE 已原样保留在 `skills/skill-detector/LICENSE`。另有方法思路参考 `lanyasheng/skill-evaluator`（该上游无许可证，逐行比对确认无成段复制）。完整核验数据见 [ATTRIBUTION.md](ATTRIBUTION.md)。

## 声明

个人业余项目，与雇主无关，不含公司内部数据、业务代码或内部文件。仓库内不含任何凭据、Token 或真实配置文件；千帆 Token 只从环境变量 `QIANFAN_BEARER_TOKEN` 读取。

## 许可

[MIT](LICENSE)。Copyright (c) 2026 luckychenxiaowen。`skill-detector` 内的上游 MIT 声明 Copyright (c) 2026 sunxingboo 原样保留。

## 发布前

`python scripts/check-before-push.py` 必须全项 PASS；新增 Skill 的规范见 [CONTRIBUTING.md](CONTRIBUTING.md)。
