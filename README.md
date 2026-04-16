# 专利写作智能体


```bash
# 安装 Claude code
npm install -g @anthropic-ai/claude-code

# 安装其他依赖
pip install -r requirements.txt

# 配置环境变量
cp .mcp.json.example .mcp.json
cp .claude/settings.local.json.example .claude/settings.local.json

# 修改 .mcp.json 中的 API KEY，包括SERPAPI_API_KEY和EXA_API_KEY
# 修改 .claude/settings.local.json 中的 Token 和 URL（配置为第三方模型，如果不使用第三方，删除掉以ANTHROPIC开头的env即可）

#CLI
claude --dangerously-skip-permissions "根据 data/输入.docx 编写专利提案 " -p  --output-format stream-json --verbose

output/temp_9ba0a678-5210-42e0-8f52-31b47bf630f6 为示例输出

```

## GitHub Copilot 使用（已整理打包）

已新增一套可直接用于 Copilot 的专利撰写 Agent 资产：

- 全局指令：`.github/copilot-instructions.md`
- 可复用 Prompt：`.github/prompts/patent-writing-agent.prompt.md`
- 技能映射：`copilot_agent_pack/skills.md`
- 案例索引：`copilot_agent_pack/cases.md`

建议顺序：
1. 在仓库中启用 Copilot （`.github/copilot-instructions.md` 会被 Copilot 自动识别为仓库级指令）
2. 使用 `patent-writing-agent.prompt.md` 发起任务
3. 按 `skills.md` 分阶段输出并检查
4. 参考 `cases.md` 中案例做格式和质量对齐

### Workflow 设计

```mermaid
graph TD
    subgraph "输入与准备阶段"
        A(用户输入: 技术资料) --> B[Input Parser: 解析关键技术点];
        B --> C[Patent Searcher: 检索现有技术];
        subgraph "工具节点"
            %% --- 增加的工具节点 ---
            C --> C1[工具: 专利搜索]
            C --> C2[工具: 论文搜索]
            %% --- 结束 ---
        end
        B --> D[Outline Generator: 生成专利大纲];
        
        %% --- 增加循环 ---
        C1 -- "重复" --> C;
        C2 -- "重复" --> C;
    end

    subgraph "核心撰写与输出"
        E[Claims Writer: 撰写权利要求]
        F[Description Writer: 撰写具体实施方式]
        
        subgraph "并行生成"
            direction LR
            G[Diagram Generator: 生成附图/流程图]
            H[Abstract Writer: 撰写摘要]
        end

        I[Markdown Merger: 合并所有部分]
        J(输出: 完整专利草稿.md)

        %% --- 内部流向 ---
        E --> F
        F --> G
        F -- "提供素材" --> H
        E -- "提供保护范围" --> H
        
        %% --- 汇合 ---
        E --> I
        F --> I
        G --> I
        H --> I
        
        I --> J
    end

    %% --- 跨子图链接 ---
    C -- "提供参考资料" --> E;
    D -- "提供文档结构" --> E;
    C -- "提供参考资料" --> F;

    %% 样式
    classDef default fill:#f9f9f9,stroke:#333,stroke-width:2px;
    classDef input fill:#E0F7FA,stroke:#00796B;
    classDef output fill:#FFECB3,stroke:#FFA000;
    
    class A,J input;
    class B,C,D,E,F,G,H,I,C1,C2 output;
```
