# 专利写作智能体（Copilot 版）

本仓库已整理为以 GitHub Copilot 为主的专利写作资产包。

## 快速使用

1. 启用仓库级指令：`.github/copilot-instructions.md`
2. 选择任务 Prompt：
   - 专利草稿生成：`.github/prompts/patent-writing-agent.prompt.md`
   - 技术交底书引导完善：`.github/prompts/technical-disclosure-guide-agent.prompt.md`
3. 按阶段参考：`copilot_agent_pack/skills.md`
4. 对照案例与规范：`copilot_agent_pack/cases.md`

## 参考资料（保留）

- 写作规范：`PATENT_SKILL.md`
- 完整样例：`data/example_patent.md`
- 架构参考：`arch.md`
- 阶段角色素材（仅作参考）：`.claude/agents/*.md`
- 阶段化历史产物：`output/temp_9ba0a678-5210-42e0-8f52-31b47bf630f6/`

## 可选依赖（仅用于文档处理）

```bash
pip install -r requirements.txt
```
