# 参考案例与素材索引（Copilot）

## 1) 完整专利样例（首选）
- 路径：`data/example_patent.md`
- 价值：
  - 提供完整章节顺序与目录样式
  - 展示“摘要-权利要求-说明书-附图”一体化输出格式
  - 可直接作为 Copilot 生成结果的结构模板

## 2) 多阶段中间产物样例
- 根目录：`output/temp_9ba0a678-5210-42e0-8f52-31b47bf630f6/`
- 价值：
  - 展示阶段化产物（01_input 到 06_final）
  - 适合复用为“分步骤产出”的检查基线
  - 可用于对比每一阶段输入/输出是否完整

## 3) 核心知识规范
- 路径：`PATENT_SKILL.md`
- 价值：
  - 覆盖发明名称、技术领域、背景技术、发明内容、实施方式、权利要求、摘要规范
  - 可作为 Copilot 写作时的统一规则底座

## 4) 角色提示词资产
- 路径（共 8 个）：
  - `.claude/agents/input-parser.md`
  - `.claude/agents/patent-searcher.md`
  - `.claude/agents/outline-generator.md`
  - `.claude/agents/abstract-writer.md`
  - `.claude/agents/claims-writer.md`
  - `.claude/agents/description-writer.md`
  - `.claude/agents/diagram-generator.md`
  - `.claude/agents/markdown-merger.md`
- 定位：仅作为 Copilot 提示词设计参考，不作为 Copilot 运行时依赖
- 价值：
  - 已拆分为 8 个高内聚（专注单一职责）写作角色
  - 可直接映射为 Copilot 分阶段提示词（作为“知识来源”而非运行时依赖）
  - 映射方法：将每个 agent 的“你的任务”段落改写为 Copilot 的阶段性指令，并保留其输入/输出约束

## 推荐使用方式
1. 先加载 `.github/copilot-instructions.md` 作为全局规则。  
2. 使用 `.github/prompts/patent-writing-agent.prompt.md` 发起任务。  
3. 写作过程中按 `copilot_agent_pack/skills.md` 逐阶段校验。  
4. 用本文件中的案例路径做结构与质量对照。  
