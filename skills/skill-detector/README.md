# skill-detector · 给 Skill 打分、做红队、找短板

解决**「这个 Skill 到底好不好、能不能发布、两个 Skill 怎么横比」**：把主观评价拆成结构检查 + 8 维打分 + 红队测试 + 多模型交叉验证 + 自主改进循环。

## 四种模式

| 模式 | 触发词 | 内容 | 依赖 |
|---|---|---|---|
| **快速**（默认） | 检测 / 评审 / 打分 | 结构检查 + 8 维打分 + 改进建议 | 无 |
| 深度 | 深度检测 / 全面审计 / 多模型 | 快速 + 红队测试 + 多模型交叉验证 | 可选 |
| 对比 | 对比 / 比较 / 排行 | 多个 Skill 并列评分 + 共性规律 | 无 |
| 改进 | 改进 / 优化 / 提升 | 深度 + 自主改进循环（带备份与回滚） | 可选 |

**8 个维度**：元数据质量、执行引导清晰度、领域知识密度、工作流完整性、输入输出清晰度、资源利用、写作质量、范围与聚焦；加权得出总分与 S/A/B/C/D 等级。结构检查按 Level 1/2/3 判定能力等级。

## 怎么用

1. 整目录复制进你的 Agent 的 `skills/` 目录
2. 说「测一下这个 Skill」→ 默认快速模式，零外部依赖
3. 需要多模型交叉验证时，三种策略自动降级：A 并行多模型 → B 千帆 API → **C 串行多视角（默认兜底，无需 Token）**

**凭据说明**：只有策略 B 需要百度千帆 Bearer Token，从 `config.json`（已 gitignore）或环境变量 `QIANFAN_BEARER_TOKEN` 读取；仓库内只有占位符示例，不含任何真实 Token。策略 C 完全不需要联网。

## 与本仓其他 Skill 怎么配合

| 顺序 | 用什么 | 得到什么 |
|---|---|---|
| 1 | `skill-writer` | 一份结构合规的 Skill |
| 2 | **本 Skill（快速模式）** | 8 维打分 + 改进建议 |
| 3 | 真实用一次 | 实际效果记录 |
| 4 | `self-evolution` | 改 / 留 / 沉淀的决策 |
| 5 | 需要深挖时回到**本 Skill（深度/改进模式）** | 红队结果 + 迭代优化 |

## 边界

- 打分是**启发式评估**，不是客观测量；不同模型、不同轮次的结果会有波动，不应当作 SLA 或排名依据。
- 红队测试用例是通用安全载荷，不构成完整安全审计；涉及生产环境请另做专业测试。
- 自主改进循环有迭代上限与早停条件，且每轮自动备份，仍建议只在工作副本上跑。

## 来源与许可（重要）

**本 Skill 不是纯自研，是基于 MIT 上游的整合改编。**

| 本地文件 | 来源 | 关系 |
|---|---|---|
| `scripts/qianfan_chat.py`、`references/dimensions.md`、`references/prompts.md`、`references/report-formats.md` | `sunxingboo/skill-evaluator`（MIT） | 逐行一致 |
| `SKILL.md`、`README.md`、`references/red-team.md`、`references/self-improve.md` | 本仓整理改写 | 原创 / 改写 |

- `LICENSE` 是上游原作者 sunxingboo 的 MIT 声明，**原样保留、未改署名**。
- `lanyasheng/skill-evaluator`（无许可证）只提供了红队测试与自主改进循环的**方法思路**；逐行比对确认无成段复制（最高仅 5 行通用测试用例载荷）。
- 完整核验数据、上游许可证状态与判定见仓根 [ATTRIBUTION.md](../../ATTRIBUTION.md) 与本目录 [ATTRIBUTION.md](ATTRIBUTION.md)。

## 文件

- `SKILL.md`、`LICENSE`、`ATTRIBUTION.md`、`README.md`
- `references/`：`dimensions.md`、`prompts.md`、`red-team.md`、`report-formats.md`、`self-improve.md`
- `scripts/qianfan_chat.py`：零第三方依赖的标准库千帆 API 客户端
