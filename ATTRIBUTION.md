# 第三方来源与许可证说明

本仓 3 个 Skill 中，`skill-writer` 与 `self-evolution` 为个人自研，未引入第三方代码或文本。`skill-detector` 含第三方来源，说明如下。

## skill-detector：基于 MIT 上游的整合改编

**结论（事实，2026-11-13 实测）**：该 Skill 不是纯自研，是基于 MIT 上游的整合改编；**可以整体按 MIT 发布**，条件是保留上游署名与许可证，并如实标注来源。

### 上游许可证核验

| 上游 | GitHub API `license` 字段 | 结论 |
|---|---|---|
| `sunxingboo/skill-evaluator` | `MIT` | 有明确许可证 |
| `lanyasheng/skill-evaluator` | `null`（未检测到） | 无明确许可证 |

### 逐文件比对结果

比对方法：把本地 8 个文件与两个上游的全部文本文件按「去除空白后长度 ≥12 的完全相同行」计算重合率，取最长重合与覆盖率。

| 本地文件 | 与 `sunxingboo`（MIT） | 与 `lanyasheng`（无许可证） |
|---|---|---|
| `scripts/qianfan_chat.py` | **131 行完全一致（覆盖率 1.000）** | 最高 5 行通用代码（0.040） |
| `references/prompts.md` | **80 行完全一致（1.000）** | 无实质重合 |
| `references/report-formats.md` | **65 行完全一致（1.000）** | 无实质重合 |
| `references/dimensions.md` | **59 行完全一致（1.000）** | 无实质重合 |
| `references/red-team.md` | 无 | 最高 5 行通用攻击载荷（0.116） |
| `references/self-improve.md` | 无 | 最高 1 行（0.032） |
| `SKILL.md` / `README.md` | 部分结构参考（4 行，0.068） | 无实质重合 |

### 判定

1. **唯一引入的第三方代码/文本来自 MIT 上游** `sunxingboo/skill-evaluator`。其 LICENSE 全文已原样保留在 `skills/skill-detector/LICENSE`，`Copyright (c) 2026 sunxingboo` 未改动，满足 MIT 第 1 条「保留版权声明与许可声明」。
2. **`lanyasheng/skill-evaluator` 只提供方法思路**（红队测试、自主改进循环的概念），本仓**未引入其代码或成段文本**：最高重合 5 行是 `'; DROP TABLE users; --`、`<script>alert('XSS')</script>` 一类业界通用安全测试用例载荷，不构成可受版权保护的实质性表达。因此本仓不因该无许可证上游产生衍生作品风险。
3. `red-team.md` / `self-improve.md` / `SKILL.md` / `README.md` 为本仓整理改写，不是上游文件的复制。
4. 本仓不含任何凭据、Token 或真实配置；千帆 API Token 仅从 `config.json`（已 gitignore）或环境变量读取，示例值为占位符。

### 若上游发生变化

若 `sunxingboo/skill-evaluator` 变更许可证，或 `lanyasheng/skill-evaluator` 补充许可证并对本仓内容提出主张，将按新情况复核；必要时替换或移除相关文件。

## 许可

- 本仓文档与自研部分：[MIT](LICENSE)，Copyright (c) 2026 luckychenxiaowen
- `skills/skill-detector/LICENSE`：MIT，Copyright (c) 2026 sunxingboo（上游原声明，原样保留）
