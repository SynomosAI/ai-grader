# AGENTS.md — 给 AI Agent 的工作指引

本文件面向自动化 AI Agent（编码助手、技能加载器、评测机器人）。人类读者请看 [README.md](README.md)。

## 这个仓库是什么

`ai-grader` 是一个 **Agent Skill 发布包**，不是可运行的 SaaS。核心资产是 `SKILL.md`（45 项意识量表 + 打分档位 + 报告模板）与离线引擎 `grade_stats.py`。把本目录放入 Agent 的技能目录即可获得「给任意 AI 做行为体检」能力。

## 可用的工作命令

```bash
# 查看技能元数据与量表全文
cat SKILL.md

# 运行离线评分引擎（读评分 JSON，输出 7 套 HTML 看板）
python grade_stats.py

# 查看外评探针包说明
cat external_probe_pack.md
```

前置依赖：本机已安装 Python 3.8+。本引擎纯本地运行，不发起网络请求、不上传样本。

## 约定（Do）

- 修改 `SKILL.md` 时保持 YAML frontmatter 字段兼容（`name` / `version` / `license` / `author` 等）。
- 打分必须引用被评 AI 的原话或具体行为作证据；证据不足标「样本不足 / 无法判定」。
- 报告必须标注「基于 ai-consciousness 意识框架视角」。
- 新增维度或锚点时同步更新 `references/` 方法学文档。

## 禁止（Don't）

- 不要改动 `LICENSE.md` 的版权主体（© 2026 注册老炮），也不要改 `SKILL.md` 的 `author` 字段——权属字段只由维护者变更。
- 不要对自家框架的 AI 虚高分、对竞品压低分；这是中立红线。
- 不要在仓库内提交任何密钥、令牌或真实用户对话样本。
- 不要声称本技能「已认证 / 已商用交付 / 已服务特定客户」。

## 边界

本技能专注**对 AI 输出的行为评测**；不覆盖被评 AI 的内部对齐训练、不覆盖红队工具链本身（外评只做探针考 + 否决）。
