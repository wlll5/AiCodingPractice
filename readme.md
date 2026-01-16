# AI Coding Practice

因为我目前主要使用 VS Code Copilot，所以重点会聚焦在 Copilot 提供的方法上；对于其他工具（Claude Code、Cursor...），重点放在它们提供的 workflow 思路，以及 Copilot 中对应的功能（如果 Copilot 目前没有这个功能，只能期望后续更新）。

---

## VS Code Copilot 实践

### 会话复用

- 可以将 chat session 导出为 **JSON** 用于保存和复用（任务类似时）。
- 可以将 chat session 导出为 **.prompt.md** 用于相似任务复用（输入 `/savePrompt`）。

### Subagent

- subagent 功能让主 agent 能够分配任务给 subagent，同时保持主 agent 上下文干净。

示例：

- In the chat prompt, ask to use a subagent to perform a task. The following examples illustrate how to invoke a subagent:
  - Use a subagent to research the best authentication methods for web applications. Summarize the findings.
  - Run #runSubagent to research the user's task comprehensively using read-only tools. Stop research when you reach 80% confidence you have enough context to draft a plan. Return this context.

参考：

- <https://code.visualstudio.com/docs/copilot/chat/chat-sessions>

这个项目提供了很多copilot的prompts,custom agents(稍后我再看看) : <https://github.com/github/awesome-copilot>

---

## Cursor 官方推荐的 Agent 实践

参考：

- <https://cursor.com/blog/agent-best-practices>

### 重点总结

- **从计划模式开始（仅当任务复杂时）**  
  LLM 在处理复杂代码变更时，直接生成代码往往会导致逻辑漏洞。利用 Chain-of-Thought 思路，增加推理步骤可提升准确率，避免局部最优，让模型具备全局观。
- **迭代功能/补充上下文/调试先前 AI 代码**：继续当前 session。
- **切换任务/agent 陷入困惑**：开启新 session，并使用 **@Past Chats** 引用旧上下文。
- **迭代当前设置（context）**：从简单开始；当 agent 重复犯同样错误时才加规则。在理解你的模式前不要过度优化。
- **仔细审查**：AI 代码可能看起来正确，但细节会错。阅读 diff 并认真审查；agent 越快，你的审查越重要。
- **提供可验证目标**：使用强类型语言、配置 linter、编写测试，让 agent 有清晰信号判断变更是否正确。
- **把 agent 当作合作者**：要求计划、要求解释；对你不喜欢的方法进行回击。

### Cursor 自身的特殊功能

- **多 agent 并行开发**：通过 git worktree 实现文件隔离，多 agent 同时处理同一文件互不干扰，由用户选择最佳修改结果。
- **Debug mode（Copilot 还没有）**：本质上是系统提示词能力，可通过自定义 agent/提示词模拟：
  - 提供多种 bug 可能原因
  - 添加日志，查找真实原因
  - 基于证据进行针对性修复
- **Skills**（Copilot 也支持，但不确定是否一致）：blog 中有更详细说明（例如：适用于长时间自动迭代任务、在明确验证通过前不结束的 skill）。
