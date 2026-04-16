# Copilot Agent Skills 映射

本文件将 Claude 子代理能力整理为 Copilot 可复用“技能阶段”。

## Skill 1: input-parser（输入解析）
- 输入：技术交底书（docx/markdown）
- 输出：结构化信息（标题、问题、现有技术、方案、效果、关键词）

## Skill 2: patent-searcher（检索分析）
- 输入：关键词与技术方案
- 输出：相似专利清单、现有技术分析、写作风格提炼

## Skill 3: outline-generator（大纲设计）
- 输入：结构化信息 + 检索分析
- 输出：专利大纲（摘要/权利要求/说明书分章目标）

## Skill 4: abstract-writer（摘要）
- 输入：大纲 + 核心方案
- 输出：规范摘要（问题、方案、效果）

## Skill 5: claims-writer（权利要求）
- 输入：大纲 + 摘要
- 输出：方法独权、从权，装置/系统、设备、介质权利要求

## Skill 6: description-writer（说明书）
- 输入：大纲 + 权利要求 + 检索分析
- 输出：技术领域、背景技术、发明内容、附图说明、具体实施方式

## Skill 7: diagram-generator（附图）
- 输入：说明书正文
- 输出：Mermaid 流程图、结构图、系统图/时序图

## Skill 8: markdown-merger（最终合并）
- 输入：摘要 + 权利要求 + 说明书 + 图表
- 输出：完整专利 markdown 草稿
