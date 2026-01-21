# 规格驱动开发 (SDD)

## 权力反转

几十年来，代码一直是王道。规格说明书（Specifications）服务于代码——它们只是我们搭建的脚手架，一旦“真正的”编码工作开始，这些脚手架就被丢弃了。我们编写 PRD 来指导开发，创建设计文档来告知实现细节，绘制图表来可视化架构。但这些始终从属于代码本身。代码是真理。其他一切充其量只是美好的愿望。代码是唯一事实来源（Source of Truth），随着代码向前演进，规格很少能跟上步伐。由于资产（代码）与实现是一体的，如果不试图基于代码构建，很难拥有并行的实现版本。

规格驱动开发（SDD）反转了这种权力结构。规格不再服务于代码——代码服务于规格。产品需求文档（PRD）不再是实现的指南；它是产生实现的源头。技术计划不再是告知编码的文档；它们是生成代码的精确定义。这不仅仅是软件构建方式的增量改进。这是对驱动开发核心动力的根本性重新思考。

自软件开发诞生以来，规格与实现之间的鸿沟就一直困扰着我们。我们试图通过更好的文档、更详细的需求、更严格的流程来弥合它。这些方法之所以失败，是因为它们承认这种鸿沟是不可避免的。它们试图缩小鸿沟，但从未消除它。SDD 通过使规格及其具体的实现计划变得“可执行”来消除这种鸿沟。当规格和实现计划直接生成代码时，鸿沟就不复存在——只剩下转换。

这种转换现在成为可能，是因为 AI 能够理解并实现复杂的规格，并创建详细的实现计划。但是，缺乏结构的原始 AI 生成会产生混乱。SDD 通过规格及随后的实现计划提供这种结构，这些计划足够精确、完整且无歧义，足以生成可工作的系统。规格成为主要产物（Artifact）。代码变成其在特定语言和框架中的表达（作为实现计划的一种实现）。

在这个新世界中，维护软件意味着演进规格。开发团队的意图通过自然语言（“**意图驱动开发**”）、设计资产、核心原则和其他准则来表达。开发的**通用语言（Lingua franca）**上升到了一个更高的层次，而代码则成为最后一公里的实现手段。

调试意味着修正那些生成了错误代码的规格及其实现计划。重构意味着为了清晰度而重组结构。整个开发工作流围绕规格作为核心事实来源进行重组，实现计划和代码作为持续生成的输出。更新 App 的新功能，因我们是创造性的个体而创建一个新的并行实现，意味着重新审视规格并创建新的实现计划。因此，这个过程是 0 -> 1, (1', ..), 2, 3, N。

开发团队将专注于他们的创造力、实验性以及批判性思维。

## 实践中的 SDD 工作流

工作流始于一个想法——通常是模糊且不完整的。通过与 AI 的迭代对话，这个想法变成一个全面的 PRD。AI 会提出澄清性问题，识别边界情况（Edge cases），并帮助定义精确的验收标准。在传统开发中可能需要数天会议和文档的工作，现在只需数小时专注的规格制定工作即可完成。这改变了传统的 SDLC——需求和设计变成了持续的活动，而非离散的阶段。这支持了一种**团队流程**，即经过团队审查的规格被表达、版本化，在分支中创建并合并。

当产品经理更新验收标准时，实现计划会自动标记受影响的技术决策。当架构师发现更好的模式时，PRD 会更新以反映新的可能性。

在整个规格制定过程中，研究智能体（Research agents）会收集关键背景信息。它们调查库的兼容性、性能基准测试和安全影响。组织约束会被自动发现并应用——你公司的数据库标准、认证要求和部署策略会无缝集成到每一个规格中。

根据 PRD，AI 生成将需求映射到技术决策的实现计划。每一个技术选择都有文档化的理由。每一个架构决策都可追溯到具体的需求。在这个过程中，一致性验证持续提高质量。AI 分析规格中的歧义、矛盾和缺口——这不再是一次性的关卡，而是持续的精炼过程。

一旦规格及其实现计划足够稳定，代码生成就开始了，但它们不必是“完成”状态。早期的生成可能是探索性的——测试规格在实践中是否合理。领域概念变为数据模型。用户故事（User stories）变为 API 端点。验收场景变为测试。这通过规格合并了开发和测试——测试场景不是在代码之后编写的，它们是生成实现和测试的规格的一部分。

反馈循环延伸到了初始开发之外。生产环境的指标和事故不仅仅触发热修复（Hotfixes）——它们会为下一次再生更新规格。性能瓶颈变成新的非功能性需求。安全漏洞变成影响所有未来生成的约束。这种在规格、实现和操作现实之间的迭代之舞，是真正理解涌现的地方，也是传统 SDLC 转变为持续演进的地方。

## 为什么 SDD 现在至关重要

三个趋势使得 SDD 不仅成为可能，而且变得必要：

首先，AI 能力已经达到一个阈值，自然语言规格可以可靠地生成工作代码。这并非要取代开发者——而是通过自动化从规格到实现的机械转换来放大他们的效能。它可以放大探索和创造力，支持轻松的“推倒重来”，并支持加法、减法和批判性思维。

其次，软件复杂性继续呈指数级增长。现代系统集成数十种服务、框架和依赖项。通过手动流程保持所有这些部分与原始意图一致变得越来越困难。SDD 通过规格驱动的生成提供系统性对齐。框架可能会演变为提供 AI 优先的支持，而非人类优先的支持，并在可重用组件周围进行架构设计。

第三，变化的速度在加快。今天的需求变更比以往任何时候都快。转型（Pivoting）不再是例外——它是预期的。现代产品开发要求基于用户反馈、市场条件和竞争压力进行快速迭代。传统开发将这些变化视为干扰。每一次转型都需要手动在文档、设计和代码中传播变更。导致的结果是：若是缓慢谨慎的更新会限制速度，若是快速鲁莽的变更则会累积技术债务。

SDD 可以支持假设/模拟（what-if）实验：“如果我们需要重新实现或更改应用程序以推广销售更多 T 恤的业务需求，我们将如何为此实施和实验？”

SDD 将需求变更从障碍转变为正常工作流。当规格驱动实现时，转型变成了系统性的再生，而非手动重写。修改 PRD 中的核心需求，受影响的实现计划会自动更新。修改用户故事，相应的 API 端点会重新生成。这不仅关于初始开发——更关于通过不可避免的变更来维持工程速度。

## 核心原则

**规格作为通用语言**：规格成为主要产物。代码成为其在特定语言和框架中的表达。维护软件意味着演进规格。

**可执行的规格**：规格必须足够精确、完整且无歧义，以生成可工作的系统。这消除了意图与实现之间的鸿沟。

**持续精炼**：一致性验证持续发生，而非作为一次性的关卡。AI 将分析规格中的歧义、矛盾和缺口视为一个持续的过程。

**研究驱动的背景**：研究智能体在整个规格制定过程中收集关键背景信息，调查技术选项、性能影响和组织约束。

**双向反馈**：生产环境的现实情况告知规格的演进。指标、事故和操作学习成为规格精炼的输入。

**用于探索的分支**：从同一规格生成多种实现方法，以探索不同的优化目标——性能、可维护性、用户体验、成本。

## 实现方法

今天，实践 SDD 需要组合现有工具并在整个过程中保持纪律。该方法可以通过以下方式实践：

- 用于迭代式规格开发的 AI 助手
- 用于收集技术背景的研究智能体
- 用于将规格转换为实现的代码生成工具
- 适应规格优先工作流的版本控制系统
- 通过 AI 分析规格文档进行一致性检查

关键在于将规格视为唯一事实来源，代码作为生成的输出服务于规格，而不是反过来。

## 使用命令简化 SDD

通过三个强大的命令来自动化`规格 → 计划 → 任务`的工作流，SDD 方法论得到了显著增强：

### `/speckit.specify` 命令

此命令将简单的功能描述（用户提示词）转换为带有自动仓库管理的完整、结构化的规格：

1. **自动功能编号**：扫描现有规格以确定下一个功能编号（例如，001, 002, 003）
2. **分支创建**：从你的描述生成语义化分支名并自动创建
3. **基于模板的生成**：复制并根据你的需求定制功能规格模板
4. **目录结构**：为所有相关文档创建正确的 `specs/[branch-name]/` 结构

### `/speckit.plan` 命令

一旦功能规格存在，此命令将创建全面的实现计划：

1. **规格分析**：读取并理解功能需求、用户故事和验收标准
2. **宪章合规**：确保与项目宪章和架构原则保持一致
3. **技术转换**：将业务需求转换为技术架构和实现细节
4. **详细文档**：生成数据模型、API 契约和测试场景的辅助文档
5. **快速入门验证**：制作包含关键验证场景的快速入门指南

### `/speckit.tasks` 命令

计划创建后，此命令分析计划及相关设计文档以生成可执行的任务列表：

1. **输入**：读取 `plan.md`（必需），以及 `data-model.md`、`contracts/`、`research.md`（如果存在）
2. **任务推导**：将契约、实体和场景转换为具体任务
3. **并行化**：标记独立任务 `[P]` 并概述安全的并行组
4. **输出**：在功能目录中写入 `tasks.md`，准备由任务 Agent 执行

### 示例：构建聊天功能

以下是这些命令如何转换传统开发工作流：

**传统方法：**

```text
1. 在文档中编写 PRD（2-3 小时）
2. 创建设计文档（2-3 小时）
3. 手动设置项目结构（30 分钟）
4. 编写技术规格（3-4 小时）
5. 创建测试计划（2 小时）
总计：~12 小时的文档工作
```

**使用命令的 SDD 方法：**

```bash
# 步骤 1：创建功能规格（5 分钟）
/speckit.specify Real-time chat system with message history and user presence

# 自动执行：
# - 创建分支 "003-chat-system"
# - 生成 specs/003-chat-system/spec.md
# - 使用结构化需求填充它

# 步骤 2：生成实现计划（5 分钟）
/speckit.plan WebSocket for real-time messaging, PostgreSQL for history, Redis for presence

# 步骤 3：生成可执行任务（5 分钟）
/speckit.tasks

# 自动创建：
# - specs/003-chat-system/plan.md
# - specs/003-chat-system/research.md (WebSocket 库比较)
# - specs/003-chat-system/data-model.md (Message 和 User 模式)
# - specs/003-chat-system/contracts/ (WebSocket 事件, REST 端点)
# - specs/003-chat-system/quickstart.md (关键验证场景)
# - specs/003-chat-system/tasks.md (源自计划的任务列表)
```

在 15 分钟内，你拥有：

- 包含用户故事和验收标准的完整功能规格
- 包含技术选择和理由的详细实现计划
- 准备好用于代码生成的 API 契约和数据模型
- 用于自动化和手动测试的综合测试场景
- 所有文档都在功能分支中正确版本化

### 结构化自动化的力量

这些命令不仅节省时间——它们强制执行一致性和完整性：

1. **无遗漏细节**：模板确保考虑每个方面，从非功能性需求到错误处理
2. **可追溯决策**：每个技术选择都链接回特定需求
3. **活体文档**：规格与代码保持同步，因为代码是由规格生成的
4. **快速迭代**：更改需求并在几分钟内（而非几天）重新生成计划

这些命令体现了 SDD 原则，即将规格视为可执行产物而非静态文档。它们将规格过程从必要的恶梦转变为开发的驱动力。

### 模板驱动的质量：结构如何约束 LLM 以获得更好结果

这些命令的真正力量不仅在于自动化，还在于模板如何引导 LLM 行为以生成更高质量的规格。模板充当复杂的提示词（Prompts），以生产性的方式约束 LLM 的输出：

#### 1. **防止过早的实现细节**

功能规格模板明确指示：

```text
- ✅ Focus on WHAT users need and WHY（关注用户需要什么以及为什么）
- ❌ Avoid HOW to implement (no tech stack, APIs, code structure)（避免如何实现——无技术栈、API、代码结构）
```

这种约束强制 LLM 保持适当的抽象级别。当 LLM 可能自然地跳转到“使用 React 和 Redux 实现”时，模板将其聚焦于“用户需要实时更新他们的数据”。这种分离确保即使实现技术发生变化，规格也能保持稳定。

#### 2. **强制显式的不确定性标记**

两个模板都强制使用 `[NEEDS CLARIFICATION]`（需要澄清）标记：

```text
When creating this spec from a user prompt:
1. **Mark all ambiguities**: Use [NEEDS CLARIFICATION: specific question]（标记所有歧义）
2. **Don't guess**: If the prompt doesn't specify something, mark it（不要猜测）
```

这防止了 LLM 做出看似合理但可能错误的假设这一常见行为。LLM 必须将“登录系统”标记为 `[NEEDS CLARIFICATION: auth method not specified - email/password, SSO, OAuth?]`，而不是猜测它使用邮箱/密码认证。

#### 3. **通过检查清单进行结构化思考**

模板包含充当规格“单元测试”的综合检查清单：

```markdown
### Requirement Completeness

- [ ] No [NEEDS CLARIFICATION] markers remain（无残留的澄清标记）
- [ ] Requirements are testable and unambiguous（需求可测试且无歧义）
- [ ] Success criteria are measurable（成功标准可衡量）
```

这些检查清单迫使 LLM 系统地自我审查其输出，捕捉可能遗漏的缺口。这就像给了 LLM 一个质量保证框架。

#### 4. **通过关卡实现的宪章合规**

实现计划模板通过阶段关卡（Phase gates）强制执行架构原则：

```markdown
### Phase -1: Pre-Implementation Gates

#### Simplicity Gate (Article VII)

- [ ] Using ≤3 projects?（使用 ≤3 个项目？）
- [ ] No future-proofing?（无过度设计/面向未来编程？）

#### Anti-Abstraction Gate (Article VIII)

- [ ] Using framework directly?（直接使用框架？）
- [ ] Single model representation?（单一模型表示？）
```

这些关卡通过让 LLM 显式地证明任何复杂性的合理性来防止过度工程。如果关卡失败，LLM 必须在“复杂性跟踪”部分记录原因，从而为架构决策建立问责制。

#### 5. **分层细节管理**

模板强制执行正确的信息架构：

```text
**IMPORTANT**: This implementation plan should remain high-level and readable.
Any code samples, detailed algorithms, or extensive technical specifications
must be placed in the appropriate `implementation-details/` file
```

这防止了规格变成不可读的代码堆砌这一常见问题。LLM 学会保持适当的细节级别，将复杂性提取到单独的文件中，同时保持主文档的可导航性。

#### 6. **测试优先思维**

实现模板强制执行测试优先开发：

```text
### File Creation Order
1. Create `contracts/` with API specifications
2. Create test files in order: contract → integration → e2e → unit
3. Create source files to make tests pass
```

这种顺序约束确保 LLM 在实现之前考虑可测试性和契约，从而产生更健壮和可验证的规格。

#### 7. **防止推测性功能**

模板明确不鼓励推测：

```text
- [ ] No speculative or "might need" features（无推测性或“可能需要”的功能）
- [ ] All phases have clear prerequisites and deliverables（所有阶段都有明确的先决条件和交付物）
```

这阻止了 LLM 添加使实现复杂化的“锦上添花”功能。每个功能必须追溯到具有明确验收标准的具体用户故事。

### 复合效应

这些约束协同工作以产生以下规格：

- **完整**：检查清单确保无遗漏
- **无歧义**：强制澄清标记突显不确定性
- **可测试**：测试优先思维融入流程
- **可维护**：适当的抽象级别和信息层级
- **可实现**：具有具体交付物的清晰阶段

这些模板将 LLM 从创意作家转变为纪律严明的规格工程师，引导其能力生成始终高质量、可执行的规格，从而真正驱动开发。

## 宪章基础：强制执行架构纪律

SDD 的核心是一部宪章（Constitution）——一套管理规格如何变为代码的不可变原则。宪章（`memory/constitution.md`）充当系统的架构 DNA，确保每个生成的实现保持一致性、简单性和质量。

### 开发九条

宪章定义了塑造开发过程各个方面的九个条款：

#### 第一条：库优先原则

每个功能必须作为独立的库开始——无例外。这强制了从一开始就进行模块化设计：

```text
Every feature in Specify MUST begin its existence as a standalone library.
No feature shall be implemented directly within application code without
first being abstracted into a reusable library component.
```

此原则确保规格生成模块化、可重用的代码，而非单体应用。当 LLM 生成实现计划时，它必须将功能构建为具有清晰边界和最小依赖的库。

#### 第二条：CLI 接口强制令

每个库必须通过命令行接口暴露其功能：

```text
All CLI interfaces MUST:
- Accept text as input (via stdin, arguments, or files)
- Produce text as output (via stdout)
- Support JSON format for structured data exchange
```

这强制了可观测性和可测试性。LLM 不能将功能隐藏在不透明的类内部——一切都必须通过基于文本的接口可访问且可验证。

#### 第三条：测试优先指令

最具变革性的条款——无测试，不代码：

```text
This is NON-NEGOTIABLE: All implementation MUST follow strict Test-Driven Development.
No implementation code shall be written before:
1. Unit tests are written
2. Tests are validated and approved by the user
3. Tests are confirmed to FAIL (Red phase)
```

这完全反转了传统的 AI 代码生成。LLM 不能生成代码并希望它能工作，而是必须首先生成定义行为的综合测试，获得批准，然后才生成实现。

#### 第七条与第八条：简单性与反抽象

这一对条款打击过度工程：

```text
Section 7.3: Minimal Project Structure
- Maximum 3 projects for initial implementation
- Additional projects require documented justification

Section 8.1: Framework Trust
- Use framework features directly rather than wrapping them
```

当 LLM 可能自然地创建复杂的抽象时，这些条款迫使它证明每一层复杂性的合理性。实现计划模板的“Phase -1 Gates”直接强制执行这些原则。

#### 第九条：集成优先测试

优先考虑真实世界的测试而非隔离的单元测试：

```text
Tests MUST use realistic environments:
- Prefer real databases over mocks
- Use actual service instances over stubs
- Contract tests mandatory before implementation
```

这确保生成的代码在实践中有效，而不仅仅是在理论上。

### 通过模板执行宪章

实现计划模板通过具体的检查点使这些条款具有可操作性：

```markdown
### Phase -1: Pre-Implementation Gates

#### Simplicity Gate (Article VII)

- [ ] Using ≤3 projects?（使用 ≤3 个项目？）
- [ ] No future-proofing?（无过度设计/面向未来编程？）

#### Anti-Abstraction Gate (Article VIII)

- [ ] Using framework directly?（直接使用框架？）
- [ ] Single model representation?（单一模型表示？）

#### Integration-First Gate (Article IX)

- [ ] Contracts defined?（契约已定义？）
- [ ] Contract tests written?（契约测试已编写？）
```

这些关卡充当架构原则的编译时检查。如果不同过关卡或在“复杂性跟踪”部分记录合理的例外情况，LLM 就无法继续。

### 不可变原则的力量

宪章的力量在于其不可变性。虽然实现细节可以演变，但核心原则保持不变。这提供了：

1. **跨时间的一致性**：今天生成的代码遵循与明年生成的代码相同的原则
2. **跨 LLM 的一致性**：不同的 AI 模型生成架构上兼容的代码
3. **架构完整性**：每个功能都加强而非破坏系统设计
4. **质量保证**：测试优先、库优先和简单性原则确保代码的可维护性

### 宪章演进

虽然原则是不可变的，但其应用可以演进：

```text
Section 4.2: Amendment Process
Modifications to this constitution require:
- Explicit documentation of the rationale for change
- Review and approval by project maintainers
- Backwards compatibility assessment
```

这允许方法论在保持稳定的同时学习和改进。宪章显示其自身带有日期的修正案，展示了原则如何基于现实世界的经验进行精炼。

### 超越规则：一种开发哲学

宪章不仅仅是一本规则手册——它是一种塑造 LLM 如何思考代码生成的哲学：

- **可观测性胜于不透明性**：一切必须通过 CLI 接口可检查
- **简单性胜于聪明**：从简单开始，仅在证明必要时增加复杂性
- **集成胜于隔离**：在真实环境中测试，而非人工环境
- **模块化胜于单体**：每个功能都是具有清晰边界的库

通过将这些原则嵌入规格和规划过程，SDD 确保生成的代码不仅功能正常——而且可维护、可测试且架构合理。宪章将 AI 从代码生成器转变为尊重并加强系统设计原则的架构合作伙伴。

## 转型

这并非关于取代开发者或自动化创造力。这是关于通过自动化机械转换来放大人类能力。这是关于创建一个紧密的反馈循环，在这个循环中，规格、研究和代码共同演进，每一次迭代都带来更深的理解以及意图与实现之间更好的对齐。

软件开发需要更好的工具来保持意图与实现的一致性。SDD 通过可执行的规格提供实现这种对齐的方法论，这些规格生成代码，而不仅仅是指导代码。
