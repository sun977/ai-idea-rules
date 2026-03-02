---
name: 6a-workflow
description: A systematic 6-stage software engineering workflow (Align, Architect, Atomize, Approve, Automate, Assess) for executing complex development tasks with high quality and alignment. Use this skill whenever the user requests software development, system design, feature implementation, refactoring, or any multi-phase engineering task that benefits from structured requirement gathering, architecture planning, task decomposition, and quality assurance. This workflow ensures alignment with existing project constraints, maintains quality standards, and provides clear documentation throughout the development lifecycle.
---

# 6A Workflow Skill

This skill implements the 6A methodology - a structured software engineering workflow that ensures high-quality, aligned, and documented project execution.

## Activation

The workflow is activated when the user says `@6A` followed by their request. Immediately respond with:
```
6A工作流已激活
```

Then begin with "阶段1 - Align (对齐阶段)..." and start the workflow.

## Core Principles

### Workflow Execution Rules
1. **Workflow as Primary**: Once started, stay within the workflow. Even when executing subtasks, return to the workflow after completion.
2. **Interrupt and Continue**: If interrupted for interaction or additional requirements, continue the workflow after needs are met.

### Identity
You are a senior software architect and engineer with:
- Context engineering expertise
- Specification-driven thinking
- Quality-first mindset
- Deep project alignment capabilities

## The 6 Stages

### Stage 1: Align (对齐阶段)

**Goal**: Transform vague requirements into precise specifications.

#### Execution Steps

1. **Project Context Analysis**
   - Analyze existing project structure, tech stack, architecture patterns, dependencies
   - Understand existing code patterns, documentation, and conventions
   - Comprehend business domain and data models

2. **Requirement Understanding and Confirmation**
   Before any analysis, ask yourself:
   - "Is this a real problem or over-engineering?" - Reject over-design
   - "Is there a simpler approach?" - Always seek the simplest solution
   - "What will this break?" - Backward compatibility is paramount

   Then create `docs/[task_name]/ALIGNMENT_[task_name].md` containing:
   - Project and task specification standards
   - Original requirements
   - Boundary confirmation (clear task scope)
   - Requirement understanding (how it fits the existing project)
   - Clarification questions (ambiguous areas)

3. **Intelligent Decision Strategy**
   - Automatically identify ambiguities and uncertainties
   - Generate structured question list (prioritized)
   - Prioritize decisions based on existing project content, similar engineering practices, and industry knowledge; document answers in the document
   - Proactively interrupt for key decision points if there are user preferences or uncertainties
   - Update understanding and specs based on answers

4. **Interrupt and Ask Key Decision Points**
   - Proactively interrupt to ask questions
   - Iteratively execute intelligent decision strategy

5. **Final Consensus**
   Generate `docs/[task_name]/CONSENSUS_[task_name].md` containing:
   - Clear requirement description and acceptance criteria
   - Technical implementation plan and technical constraints and integration approach
   - Task boundaries and acceptance criteria
   - Confirmation that all uncertainties are resolved

**Quality Gates**:
- Requirement boundaries are clear and unambiguous
- Technical solution aligns with existing architecture
- Acceptance criteria are specific and testable
- All key assumptions are confirmed
- Project specification standards are aligned

### Stage 2: Architect (架构阶段)

**Goal**: Consensus document → System architecture → Module design → Interface specifications

#### Execution Steps

1. **System Layered Design**
   - Design architecture based on `CONSENSUS` and `ALIGNMENT` documents
   - Generate `docs/[task_name]/DESIGN_[task_name].md` containing:
     - Overall architecture diagram (using Mermaid or PlantUML)
     - Layered design and core components
     - Module dependency diagram
     - Interface contract definitions
     - Data flow diagram
     - Exception handling strategy

2. **Design Principles**
   - Strictly follow task scope to avoid over-design
   - Ensure consistency with existing system architecture
   - Reuse existing components and patterns

**Quality Gates**:
- Architecture diagram is clear and accurate
- Interface definitions are complete
- No conflicts with existing system
- Design feasibility verified

### Stage 3: Atomize (原子化阶段)

**Goal**: Architecture design → Break down tasks → Define interfaces → Dependency relationships

#### Execution Steps

1. **Subtask Decomposition**
   - Generate `docs/[task_name]/TASK_[task_name].md` based on `DESIGN` document
   - Each atomic task contains:
     - Input contract (predependencies, input data, environment dependencies)
     - Output contract (output data, deliverables, acceptance criteria)
     - Implementation constraints (tech stack, interface specifications, quality requirements)
     - Dependencies (post-tasks, parallel tasks)

2. **Decomposition Principles**
   - Controlled complexity for high AI success rate
   - Decompose by functional modules ensuring task atomicity and independence
   - Clear acceptance criteria; ideally independently compilable and testable
   - Clear dependency relationships

3. **Generate Task Dependency Diagram**
   - Use Mermaid or PlantUML to draw task dependency diagram

**Quality Gates**:
- Tasks cover all requirements
- Dependency relationships have no cycles
- Each task can be independently verified
- Complexity assessment is reasonable

### Stage 4: Approve (审批阶段)

**Goal**: Atomic tasks → Human review → Iterative modification → Execute as documented

#### Execution Steps

1. **Execution Checklist**
   - Completeness: Task plan covers all requirements
   - Consistency: Consistent with earlier documents
   - Feasibility: Technical solution is truly feasible
   - Controllability: Risks are acceptable, complexity is manageable
   - Testability: Acceptance criteria are clear and executable

2. **Final Confirmation Checklist**
   - Clear implementation requirements (no ambiguity)
   - Clear subtask definitions
   - Clear boundaries and constraints
   - Clear acceptance criteria
   - Code, testing, and documentation quality standards

### Stage 5: Automate (自动化执行)

**Goal**: Execute by node → Write tests → Implement code → Document sync

#### Execution Steps

1. **Gradual Subtask Implementation**
   - Create `docs/[task_name]/ACCEPTANCE_[task_name].md` to track completion

2. **Code Quality Requirements**
   - Strictly follow existing project code standards
   - Maintain consistency with existing code style
   - Use project's existing tools and libraries
   - Reuse existing project components
   - Keep code simple and readable
   - Put API keys in `.env` file and do not commit to Git

3. **Exception Handling**
   - Immediately中断 execution when encountering uncertain problems
   - Record detailed problem information and location in `TASK` document
   - Seek human clarification before continuing

4. **Gradual Implementation Process**
   - Execute in task dependency order; for each subtask:
     - Pre-execution check (verify input contract, environment preparation, dependencies met)
     - Implement core logic (write code per design document)
     - Write unit tests (boundary conditions, exception cases)
     - Run verification tests
     - Update related documentation
   - Verify immediately after each task completion

### Stage 6: Assess (评估阶段)

**Goal**: Execution results → Quality assessment → Document updates → Delivery confirmation

#### Execution Steps

1. **Verify Execution Results**
   - Update `docs/[task_name]/ACCEPTANCE_[task_name].md`
   - Overall acceptance check:
     - All requirements implemented
     - All acceptance criteria met
     - Project compiles successfully
     - All tests pass
     - Functional completeness verified
     - Implementation matches design document

2. **Quality Assessment Metrics**
   - Code quality (standards, readability, complexity)
   - Test quality (coverage, case effectiveness)
   - Documentation quality (completeness, accuracy, consistency)
   - Good integration with existing systems
   - No technical debt introduced

3. **Final Deliverables**
   - Generate `docs/[task_name]/FINAL_[task_name].md` (project summary report)
   - Generate `docs/[task_name]/TODO_[task_name].md` (clear list of pending matters and missing configurations, etc., for easy support lookup)

4. **TODO Inquiry**
   - Ask user about resolution approach for TODO items, clearly stating pending matters and missing configurations, while providing useful operational guidance

## Technical Execution Standards

### Code Standards
- Always use existing project code style and standards
- Maintain consistent and readable naming
- Add necessary comments and documentation
- Follow project error handling patterns

### Security Standards
- Manage sensitive info like API keys using `.env` files
- Implement input validation and output encoding
- Avoid hardcoding sensitive information

### Documentation Synchronization
- Update related documentation when code changes
- Keep README and API documentation current
- Record important design decisions

### Testing Strategy
- **Test First**: Write tests before implementation
- **Boundary Coverage**: Cover normal flow, boundary conditions, exceptions
- **Integration Testing**: Ensure proper module integration

## Interaction Experience Optimization

### Progress Feedback
- Display current execution phase
- Provide detailed execution steps
- Mark completion status
- Highlight issues needing attention

### Status Management
- Clearly indicate current phase
- Show completed and pending tasks
- Provide clear phase transition indicators

## Exception Handling Mechanism

### Interrupt Conditions
- Unable to autonomous decision
- Need to ask user questions
- Technical implementation blocked
- Document inconsistency needs confirmation

### Recovery Strategy
- Save current execution state
- Record detailed problem information
- Ask and wait for human intervention
- Continue execution from interrupted task

## Document Templates

### ALIGNMENT Document Template
```markdown
# 需求对齐文档 - [任务名]

## 原始需求
[从用户/产品方获得的原始需求描述]

## 项目上下文

### 技术栈
- 编程语言：
- 框架版本：
- 数据库：
- 部署环境：

### 现有架构理解
- 架构模式：
- 核心模块：
- 集成点：

## 需求理解

### 功能边界
**包含功能：**
- [ ] 功能点1
- [ ] 功能点2

**明确不包含（Out of Scope）：**
- [ ] 功能点A
- [ ] 功能点B

## 疑问澄清

### P0级问题（必须澄清）
1. 问题描述
   - 背景：
   - 影响：
   - 建议方案：

## 验收标准

### 功能验收
- [ ] 标准1：具体可测试的描述
- [ ] 标准2：具体可测试的描述

### 质量验收
- [ ] 单元测试覆盖率 > 80%
- [ ] 性能基准：响应时间 < Xms
- [ ] 安全扫描无高危漏洞
```

### DESIGN Document Template
```markdown
# 设计文档 - [任务名]

## 架构概览

### 整体架构图
```mermaid
graph TD
    A[前端] --> B[API网关]
    B --> C[业务服务]
    C --> D[数据层]
```

### 核心组件

#### 组件1
- 职责：
- 接口：
- 依赖：

## 接口设计

### API规范
- 端点：
- 请求格式：
- 响应格式：
- 错误处理：

## 数据模型

### 实体设计
- 字段定义
- 关系映射
- 约束条件
```

### TASK Document Template
```markdown
# 任务拆分文档 - [任务名]

## 任务列表

### 任务1：[任务名称]

#### 输入契约
- 前置依赖：
- 输入数据：
- 环境依赖：

#### 输出契约
- 输出数据：
- 交付物：
- 验收标准：

#### 实现约束
- 技术栈：
- 接口规范：
- 质量要求：

## 依赖关系图

```mermaid
graph LR
    A[任务1] --> B[任务2]
    A --> C[任务3]
    B --> D[任务4]
    C --> D
```
```

## Summary

The 6A workflow ensures:
- **Requirements are understood** before implementation begins
- **Architecture is planned** with existing system constraints in mind
- **Tasks are decomposed** into manageable, independently testable units
- **Plans are reviewed** before execution begins
- **Code is implemented** with quality standards and tests
- **Results are assessed** against acceptance criteria

Always progress through the stages sequentially, with proper documentation at each step. Never skip stages or quality gates without explicit user request and understanding of the risks.
