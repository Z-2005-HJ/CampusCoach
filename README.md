# CampusCoach

CampusCoach 是面向成年初学者的健身、饮食和生活方式信息整理与执行辅助产品。

当前阶段：Development Harness 第 1 步已完成，建立了 Git 仓库基线和 Coding Agent
工作契约。项目业务代码、Python 环境和自动化检查尚未建立，将在后续步骤中完成。

## 文档入口

开始开发前，按以下顺序阅读：

1. [CAMPUSCOACH_PLAN.md](CAMPUSCOACH_PLAN.md)：产品需求、边界和阶段规划。
2. [AGENTS.md](AGENTS.md)：Coding Agent 必须遵守的工作规则。
3. [HARNESS.md](HARNESS.md)：Development Harness 的执行闭环和验收要求。
4. [docs/README.md](docs/README.md)：项目文档目录和建设记录入口。

文档之间出现冲突时，以 `CAMPUSCOACH_PLAN.md` 中已经确认的产品约束为准，并停止
可能扩大产品范围或改变安全行为的实现。

## 当前状态

第 1 步已经建立以下基线：

- Git 版本管理和 `main` 分支。
- 项目说明与文档导航。
- Development Harness 工作闭环。
- Coding Agent 的项目边界、安全要求、修改规则和停止条件。
- 缓存、本地配置、敏感文件和构建产物的忽略规则。
- 环境变量示例，不包含真实密钥。
- `docs/` 基础目录和第 1 步详细验收记录。

当前仓库还没有可运行的服务。不要在 README 中把后续计划写成已经可用的命令。

## 本地运行

本地安装、启动、测试和检查命令将在 Harness 第 2 步落地，并统一记录在本文档中。

在对应命令建立并完成验证前：

- 不要假设项目已有可运行的 Python 环境。
- 不要使用未经仓库记录的临时命令作为正式验证结果。
- 不要提前引入产品业务代码、数据库或前端实现。

## 开发工作方式

1. 先阅读产品规划、本文件、`AGENTS.md` 和相关功能规格。
2. 在任务开始前明确任务 ID、目标、范围和验证方式。
3. 只修改任务所需的最小范围。
4. 使用自动化测试和质量门禁验证结果。
5. 记录实际执行的命令、结果、风险和尚未完成的事项。
6. 只有证据完整且检查通过的任务才能标记为完成。

具体执行要求见 [HARNESS.md](HARNESS.md) 和 [AGENTS.md](AGENTS.md)。

## 技术与范围基线

- 运行环境方向：Python 3.12、uv。
- 后端方向：FastAPI、Pydantic v2。
- 业务控制：确定性 Python 规则，不使用模型替代安全门、计划状态或数值计算。
- 初始架构：模块化单体，先建立清晰边界，不提前拆分微服务。
- 测试方向：pytest、Ruff，页面阶段再接入 Playwright。

当前只建设 Development Harness。供产品内模型使用的 Runtime Harness 按产品规划
留到阶段八实现。

## 安全与数据边界

- 普通训练计划仅面向 18 岁及以上用户。
- 高风险输入必须先阻断普通训练和减脂建议。
- 未知、缺失和未确认的数据不得被当作事实、零值或无风险状态。
- 未完成独立审核的医疗阈值、训练递进阈值和个人营养目标规则不得由 Agent 编造。
- 测试、演示和公开材料只能使用合成数据。
- 不得提交真实健康资料、身份信息、令牌、密钥或私人上传文件。

## 目录结构

```text
CampusCoach/
├── .env.example
├── .gitattributes
├── .gitignore
├── AGENTS.md
├── CAMPUSCOACH_PLAN.md
├── HARNESS.md
├── README.md
└── docs/
    ├── README.md
    └── harness/
        └── step-01-repository-and-agent-contract.md
```

后续步骤会按需增加 `src/`、`tests/`、`docs/specs/`、`docs/tasks/`、
`docs/adr/` 和 `docs/worklog/`。这些目录在对应步骤建立前不虚构内容。

## Git 基线

- 默认分支：`main`
- 远程仓库：`https://github.com/Z-2005-HJ/CampusCoach.git`
- 首次基线提交：建立仓库契约和第 1 步验收记录

提交前必须确认没有敏感文件和真实用户数据。工作区应保持干净，除非正在执行一项
有明确范围的任务。
