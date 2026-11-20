# Harness 第 1 步：仓库与 Agent 工作契约

日期：2026-11-20

状态：已通过

## 1. 目标

建立项目版本管理基线，以及 Coding Agent 在 CampusCoach 中必须遵守的工作规则。

## 2. 范围

本步骤只建立：

- Git 仓库和 `main` 分支基线。
- 项目说明和文档入口。
- Development Harness 的执行闭环与验收要求。
- Agent 的项目边界、安全要求、修改规则、停止条件和验证规则。
- 本地忽略规则和环境变量示例。
- `docs/` 基础目录。
- 首次基线提交。

## 3. 非目标

- 不建立 Python 3.12 或 uv 环境。
- 不创建 FastAPI 应用或健康检查。
- 不创建 pytest、Ruff 或统一检查命令。
- 不建立规格、任务和架构决策模板。
- 不建立正式工作记录模板。
- 不接入 CI。
- 不实现任何 CampusCoach 业务功能。
- 不实现产品 Runtime Harness。

## 4. 产物

| 文件 | 用途 |
| --- | --- |
| `README.md` | 项目入口、当前状态和文档导航 |
| `HARNESS.md` | 开发 Harness 的目标、质量门禁和验收规则 |
| `AGENTS.md` | Coding Agent 工作契约 |
| `.gitattributes` | 统一文本换行规则，避免跨平台提交产生无意义差异 |
| `.gitignore` | 排除缓存、本地配置、敏感文件和构建产物 |
| `.env.example` | 环境变量名称和占位值，不包含密钥 |
| `docs/README.md` | 文档目录说明 |
| 本文件 | 第 1 步范围和验收证据 |

## 5. 已落实的决定

1. Development Harness 与产品 Runtime Harness 分开建设。
2. 当前只完成开发 Harness 的仓库和 Agent 工作契约。
3. 产品规划是业务规则的权威来源，聊天历史不能替代规格。
4. Agent 不得编造产品规则、医疗阈值、营养事实或数据来源。
5. 规格不完整且保守处理仍会改变业务结果时，必须停止并记录缺口。
6. 任务状态统一为 `proposed`、`ready`、`in_progress`、`blocked`、
   `verifying` 和 `done`。
7. 失败、阻塞、未运行和通过必须明确区分。
8. 测试、演示和公开材料只使用合成数据。
9. 当前没有应用和检查命令；后续命令必须在 README 中建立并验证。
10. 产品 Runtime Harness 按产品规划留到阶段八。

## 6. 验收清单

- [x] Git 仓库可正常提交，`main` 分支和远程仓库配置正确。
- [x] 工作区在提交后保持干净。
- [x] 文档区分 Development Harness 和 Runtime Harness。
- [x] 文档明确禁止 Agent 编造产品规则、医疗阈值、营养事实和数据来源。
- [x] 文档规定规格不完整时的停止和记录规则。
- [x] 文档定义任务状态、失败处理、停止条件和完成定义。
- [x] 文档要求测试和演示只使用合成数据。
- [x] README 标明统一安装、启动、测试和检查命令将在第 2 步建立。
- [x] 仓库不包含虚拟环境、缓存、密钥、真实健康资料或身份信息。
- [x] 文档规则与 `CAMPUSCOACH_PLAN.md` 没有冲突。
- [x] 新 Agent 只阅读仓库即可知道当前状态和下一步。
- [x] 首次基线提交已创建并推送到远程 `main`。

## 7. 验证命令和结果

执行环境：Windows PowerShell，Git 本地提交身份仅在当前仓库配置。

### 7.1 文件和提交检查

结果：

- `git init -b main` 成功，远程 `origin` 指向
  `https://github.com/Z-2005-HJ/CampusCoach.git`。
- `git status --short --untracked-files=all` 返回 8 个预期文件，无额外产物。
- 初次提交为 `chore: establish repository and agent working contract`。
- 推送后 `main` 跟踪 `origin/main`，工作区干净。

### 7.2 忽略规则检查

结果：

- `.env` 命中 `.gitignore:37`，未被提交。
- `.venv/pyvenv.cfg` 命中 `.gitignore:6`，未被提交。
- `__pycache__/x.pyc` 命中 `.gitignore:2`，未被提交。
- `.env.example` 命中 `.gitignore:39` 的反向规则，正常纳入版本控制。

### 7.3 敏感信息和禁止内容检查

结果：

- 使用 `rg` 扫描 AWS Access Key、私钥头、GitHub Token 和 `sk-` 形态字符串，未发现
  凭据形态内容。
- 使用 `rg` 扫描真实健康资料、真实姓名、手机号和身份证标识，未发现内容。
- `.env.example` 只包含占位值和空观测配置，未包含可用密钥。

### 7.4 文档一致性检查

结果：

- 文档明确将 Development Harness 与产品 Runtime Harness 分开，后者留到产品阶段八。
- 文档保留产品规划中的 18 岁门槛、安全阻断、用户确认、未知数据保守处理和合成
  数据要求。
- 文档没有新增产品范围，没有编造动作库、营养阈值、医疗阈值或个人目标规则。
- README 明确说明当前没有可运行应用和检查命令，避免把后续步骤写成已实现。

## 8. 已知限制

- 当前没有 Python 环境、应用入口、测试或代码检查。
- 当前忽略规则覆盖后续常见产物，但会随技术栈实际落地继续调整。
- 正式规格、任务、架构决策和工作记录模板尚未建立。
- 远程 CI 尚未接入。

## 9. 下一步入口

第 1 步通过并经用户确认后，进入 Harness 第 2 步：建立可复现的 Python 3.12 与 uv
环境、最小 FastAPI 应用和基础测试入口。

在第 2 步建立可执行命令前，不得把本文件中的预期命令视为已实现能力。
