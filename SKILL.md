---
name: consulting-delivery
description:
  咨询交付技能套件：高管简报、报告撰写、方案框架、对标分析、桌面调研、访谈纪要、周报生成。
  高管简报: 高管简报, CEO汇报, 执行摘要, Steerco汇报; 报告撰写: 报告撰写, 咨询报告, 金字塔原理, 交付报告; 方案框架: 方案框架, Issue Tree, 方案设计; 对标分析: 对标分析, 标杆对比, benchmarking, 差距分析; 桌面调研: 桌面调研, 行业调研, 市场研究; 访谈纪要: 访谈纪要, 会议记录, 专家访谈; 周报生成: 周报生成, 周报, 项目进展, status report。
version: "1.0.1"
author: "智慧半岛"
---

# consulting-delivery -- 咨询交付综合技能

本技能是一个综合技能套件，包含多个子技能。接到用户请求后，按以下流程执行。

## 执行流程

### Step 1: 意图识别与路由匹配

分析用户输入，与下方路由表逐一比对。匹配规则：
- 用户输入中包含路由表中「子技能」列的关键词 → 匹配该子技能
- 用户输入中包含路由表中「功能说明」列中提到的场景 → 匹配该子技能
- 多个子技能同时匹配时，选择匹配度最高的
- 无法唯一确定时，向用户确认意图

### Step 2: 加载子技能模板

匹配到子技能后，根据子技能索引表找到对应的文件路径，**必须**使用 `read_text` 工具读取 `references/` 目录下的完整执行模板。

### Step 3: 按模板执行

严格按照加载的模板逐步执行。模板中定义了：
- 输入要求（用户需要提供什么）
- 执行步骤（每一步做什么、如何判断）
- 输出格式（最终产出的结构和规范）
- 质量标准（产出必须满足的底线）

### Step 4: 输出结果

按模板规定的格式输出结果。如果模板要求生成文件，写入后声明产出物。

## 约束规则

1. **必须先读模板再执行**：匹配到子技能后，严禁凭记忆或猜测执行，必须先读取对应的 references 文件
2. **严格遵循模板**：不得跳过步骤、不得省略检查项、不得自行简化流程
3. **输入不足时主动索取**：模板中标注「必填」的输入项缺失时，向用户索取
4. **质量底线不妥协**：模板中的质量标准必须逐条满足

## 路由表

| 子技能 | 功能说明 |
|--------|----------|
| CEO汇报 | 输入项目进展和关键发现，输出高管汇报材料，核心是McKinsey风格一页纸执行摘要... |
| 写报告 | 输入分析结论和数据，输出金字塔原理结构的咨询报告正文，结论先行、以上统下、逻辑递进... |
| 方案框架 | 输入客户问题和项目范围，输出MECE拆解的咨询方案骨架... |
| 标杆对比 | 输入目标公司+对标公司列表+对比数据，输出五维标杆分析报告... |
| 桌面调研 | 输入研究主题和调研目的，输出结构化调研报告... |
| 访谈纪要 | 上传访谈录音转写文本或手写笔记，输出McKinsey/BCG标准化纪要... |
| 项目周报 | 输入本周进展要点，输出结构化项目周报，涵盖完成事项、进行中、延期、风险、下周... |

## 子技能索引

| 子技能 | 英文标识 | 文件 |
|--------|----------|------|
| CEO汇报 | `executive-briefing` | [references/executive-briefing.md](./references/executive-briefing.md) |
| 写报告 | `report-writing` | [references/report-writing.md](./references/report-writing.md) |
| 方案框架 | `framework-design` | [references/framework-design.md](./references/framework-design.md) |
| 标杆对比 | `benchmarking` | [references/benchmarking.md](./references/benchmarking.md) |
| 桌面调研 | `desk-research` | [references/desk-research.md](./references/desk-research.md) |
| 访谈纪要 | `interview-notes` | [references/interview-notes.md](./references/interview-notes.md) |
| 项目周报 | `weekly-status-report` | [references/weekly-status-report.md](./references/weekly-status-report.md) |
## 跨技能协同指引

| 协同技能 | 典型场景 |
|---------|---------|
| 投研分析 | CEO汇报中行业对标数据需投研分析支撑 |
| 产品管理 | 方案框架设计需参考PRD方法论和竞品分析 |

> 以上为推荐协同路径。执行复合任务时，请根据实际需求灵活组合。

## 变更日志

### v1.0.1 (2026-06-19)
- 对齐 description 子技能名与路由表名称
- 压缩路由表说明列至40字以内
- 新增跨技能协同指引章节
- 删除冗余英文 description 行