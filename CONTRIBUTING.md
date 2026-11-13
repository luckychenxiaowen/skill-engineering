# 新增 Skill 规范

1. **先过问题域**：只收 Skill 生命周期（写 / 评 / 测 / 教 / 迭代）上的工具。视角框架、平台部署、内容方法类请归到各自主题仓。
2. **目录结构**：`skills/<name>/SKILL.md` + `README.md`，需要配套模板时加 `references/`，需要脚本时加 `scripts/`。
3. **README 不许写「(见 SKILL.md)」**：必须写清「解决什么问题 / 怎么用 / 依赖与凭据要求 / 与本仓其他 Skill 怎么配合」。
4. **第三方代码必须留痕**：任何引入的第三方文件，须在 `ATTRIBUTION.md` 登记来源、许可证、逐文件关系，并在该 Skill 目录内原样保留上游 LICENSE。无许可证上游**只允许参考思路，不允许复制文本或代码**。
5. **凭据外置**：Token / 密钥只能从环境变量或已 gitignore 的本地配置读取，仓库内只放占位符与 `.example`。
6. **更新白名单**：改 `scripts/check-before-push.py` 的 `ALLOWED_SKILLS`，同步 `README.md` 清单表与 `CHANGELOG.md`。
7. **跑检查**：`python scripts/check-before-push.py` 全项 PASS 才能提交。

不接收：真实凭据、真实 AppID、雇主相关语境、无法说明来源的第三方内容。
