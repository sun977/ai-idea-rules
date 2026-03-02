# Documentation Templates Reference

This file contains detailed templates and schemas for each document type used in the 6A workflow.

## ALIGNMENT Document Schema

```yaml
# ALIGNMENT_[task_name].md
title: "需求对齐文档 - [task_name]"
sections:
  - 原始需求
  - 项目上下文
    - 技术栈
    - 现有架构理解
  - 需求理解
    - 功能边界
    - 明确不包含
  - 疑问澄清
    - P0级问题
    - P1级问题
  - 验收标准
    - 功能验收
    - 质量验收
```

## CONSENSUS Document Schema

```yaml
# CONSENSUS_[task_name].md
title: "共识文档 - [task_name]"
sections:
  - 需求确认
  - 技术方案
  - 解决约束
  - 验收标准
  - 假设确认
```

## DESIGN Document Schema

```yaml
# DESIGN_[task_name].md
title: "设计文档 - [task_name]"
sections:
  - 架构概览
    - 整体架构图
  - 核心组件
  - 接口设计
  - 数据模型
  - 异常处理
```

## TASK Document Schema

```yaml
# TASK_[task_name].md
title: "任务拆分文档 - [task_name]"
sections:
  - 任务列表
    - [每个任务的输入契约、输出契约、实现约束]
  - 依赖关系图
```

## ACCEPTANCE Document Schema

```yaml
# ACCEPTANCE_[task_name].md
title: "验收跟踪文档 - [task_name]"
sections:
  - 执行记录
  - 验收检查
  - 问题记录
```

## FINAL Document Schema

```yaml
# FINAL_[task_name].md
title: "项目总结 - [task_name]"
sections:
  - 执行总结
  - 交付清单
  - 技术债务
  - 后续建议
```

## TODO Document Schema

```yaml
# TODO_[task_name].md
title: "待办事项 - [task_name]"
sections:
  - 待完成功能
  - 需要补充配置
  - 文档更新
  - 其他事项
```
