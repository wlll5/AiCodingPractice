## Spec-driven development
参考链接:
<https://github.blog/ai-and-ml/generative-ai/spec-driven-development-with-ai-get-started-with-a-new-open-source-toolkit/>
<https://github.com/github/spec-kit?tab=readme-ov-file#-get-started>
<https://github.com/github/spec-kit/blob/main/spec-driven.md>

- 使用总结:
 - /speckit.constitution create your project's governing principles and development guidelines that will guide all subsequent development
   - eg./speckit.constitution Create principles focused on code quality, testing standards, user experience consistency, and performance requirements
 - /speckit.specify describe what you want to build. Focus on the what and why, not the tech stack
   - eg. /speckit.specify Build an application that can help me organize my photos in separate photo albums. Albums are grouped by date and can be re-organized by dragging and dropping on the main page. Albums are never in other nested albums. Within each album, photos are previewed in a tile-like interface.
 - /speckit.clarify Identify underspecified areas in the current feature spec by asking up to 5 highly targeted clarification questions and encoding answers back into the spec. (不需要额外提示词)
 - /speckit.plan provide your tech stack and architecture choices
   - eg. /speckit.plan The application uses Vite with minimal number of libraries. Use vanilla HTML, CSS, and JavaScript as much as possible. Images are not uploaded anywhere and metadata is stored in a local SQLite database.
 - /speckit.tasks to create an actionable task list from your implementation plan (不需要额外提示词)
 - /speckit.implement to execute all tasks and build your feature according to the plan (不需要额外提示词)

以"优化当前小程序美术"为例，推荐的 speckit 工作流顺序：            
  1. /speckit.specify    ← 先用这个，把需求描述写成规格文档 (spec.md)                   
  2. /speckit.clarify    ← （可选）让 AI 提问来补全规格中的模糊点                     
  3. /speckit.plan       ← 生成技术方案 (research.md, data-model.md 等)                 
  4. /speckit.tasks      ← 根据方案拆成有依赖关系的任务列表 (tasks.md)                  
  5. /speckit.analyze    ← （可选）交叉检查 spec/plan/tasks 的一致性                    
  6. /speckit.implement  ← 按任务列表逐个实现

  简单来说核心流程就是 4 步：

  specify → plan → tasks → implement

  clarify、analyze、checklist
  是可选的质量检查环节，看需求复杂度决定要不要用。taskstoissues 是把任务发到 GitHub   
  Issues，个人项目一般用不上。

### plan是必须的吗

看需求类型

  plan 阶段会生成 research.md、data-model.md、API契约这些技术设计产物。对于"优化小程序美术"这种纯
  UI/视觉调整的需求，大概率不涉及数据模型和接口变更，plan 产出的大部分内容都是多余的。
  
  但 tasks 命令会读取 plan.md 作为输入来拆任务，所以：
  - 需求涉及后端/数据/接口 → plan 必须走
  - 纯前端/UI 调整 → 可以跳过 plan，直接从 specify 到 tasks（tasks 也能只基于 spec.md 
  生成，只是拆得没那么细）

  你这个"优化美术"的场景，我建议：specify → tasks → implement跳过 plan 就够了。

### 比方说我想让claude根据某个skill来进行ui优化,我应该在哪一步要求使用skill?            

在 specify 这一步。                                                                 
  
  /speckit.specify 接受自然语言描述作为输入，你在描述需求时直接告诉它参考哪个 skill就行。比如:
  - 优化小程序 UI 美术风格，参考 /xxx-skill 的设计规范

  这样 skill 的约束会被写进 spec.md，后续 tasks 和 implement 都会自动遵循。

  如果是在 implement 阶段才引入 skill，前面拆出来的任务可能跟 skill
  的要求对不上，还得返工。越早引入约束越好
