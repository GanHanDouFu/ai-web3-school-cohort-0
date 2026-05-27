# AI × Web3 School - 学习仓库

个人学习记录与 proof-of-work 工作区，用于 AI × Web3 School 的学习打卡、笔记沉淀和 Handbook 反馈。

## 学员信息

- **AI 基础**：有基础（熟悉 ChatGPT/Claude，了解 Prompt）
- **Web3 基础**：新手
- **编程能力**：会基础脚本
- **目标方向**：开发
- **每日学习时间**：2-3 小时
- **开始日期**：2026-05-23

## 相关链接

- [Handbook](https://aiweb3.school/zh/handbook/)
- [WCB 课程页面](https://web3career.build/zh/programs/AI-Web3-School)
- [WCB Learning 页面](https://web3career.build/zh/programs/AI-Web3-School#tab=learning)
- [GitHub 仓库](https://github.com/GanHanDouFu/ai-web3-school-cohort-0)

## 目录说明

| 目录 | 用途 |
|------|------|
| `daily/` | 每日学习笔记与打卡草稿 |
| `tasks/` | 课程任务记录 |
| `experiments/` | 实验与练习 |
| `handbook-feedback/` | Handbook 的问题反馈与建议 |
| `hackathon/` | 黑客松项目 |
| `submissions/` | 提交的作业和项目 |
| `templates/` | 笔记模板 |
| `week1/` | Week 1 学习成果 |

## Week 1 完成情况

### 模块 A：AI 基础 ✅

- [x] 理解 LLM 基本工作方式（概率生成、上下文窗口）
- [x] 理解四个控制层面（上下文、系统指令、提示词、工具调用）
- [x] 理解 Prompt → Workflow → Agent 边界
- [x] 理解 AI 输出验证的必要性（幻觉、引用错误、推理漂移）
- [x] 理解 Agent 核心技术组件（状态、记忆、MCP、Tool Calling、Tracing）
- [x] 搭建 Learning Agent（Claude Code）
- [x] 完成一次 Agent 协助学习任务

### 模块 B：Web3 基础 ✅

- [x] 理解账户、地址、钱包的关系（助记词 → 私钥 → 公钥 → 地址）
- [x] 理解签名与交易的关系（签名 = 授权具体动作）
- [x] 理解 Gas 机制（计算成本、激励验证者、L1 vs L2）
- [x] 理解智能合约 vs 普通后端（状态公开、执行透明、不可随意修改）
- [x] 理解主网 vs 测试网（学习先用测试网）
- [x] 理解区块浏览器的作用（查询交易、验证状态）
- [x] 了解账户抽象、智能账户、多签等高级概念

### 模块 C：最小交叉实验 ✅

- [x] 设计 AI 输出 → 人工复核 → 钱包确认 → 链上执行 → 区块验证 流程
- [x] 理解每个环节的风险和应对措施
- [x] 生成可交互学习产物（Web3 概念测验）

### Web3 实操 ✅

- [x] 创建测试钱包（MetaMask）— 地址：`0xF0cf20f5821fFe917F24532075E2FAC81b580c2e`
- [x] 领取 Sepolia 测试币 — 来源：sepolia-faucet.pk910.de
- [x] 发送一笔测试交易 — [TxHash](https://sepolia.etherscan.io/tx/0x38e6576618bc71ab8ad8c5be9de8563e42ccc2dd02c479e4dac12c68b899d1b0)
- [x] 部署一个最小智能合约 — [合约地址](https://sepolia.etherscan.io/address/0x8df998f592de1321b62ee661fc9045c3af29b1e8)
- [x] 完成一次合约读写 — set(42) / get() → 42 — [TxHash](https://sepolia.etherscan.io/tx/0x2bdbe4adb57024ba652eedb52886507ae09a5cd2e9f32c700633003e6c7d8ba2)

## Learning Agent 配置

- **工具**：Claude Code (Anthropic CLI)
- **模型**：Claude Opus 4.7
- **使用场景**：
  - 课程资料整理与概念解释
  - 学习笔记生成
  - 代码生成（Solidity、HTML/JS）
  - Prompt 工程实践
  - GitHub repo 维护

## Week 1 产出

| 文件 | 说明 |
|------|------|
| `week1/notes/module-a-ai-basics.md` | AI 基础概念笔记 |
| `week1/notes/module-b-web3-basics.md` | Web3 基础概念笔记 |
| `week1/notes/module-c-crossover-experiment.md` | 交叉实验设计 |
| `week1/prompts/learning-agent-prompt.md` | Agent 使用记录 |
| `week1/logs/agent-session-01.md` | Agent 学习日志 |
| `week1/demos/web3-concept-quiz.html` | Web3 概念测验（可交互） |

## 隐私提醒

本仓库为 public，请勿放入以下内容：
- API Key、助记词、私钥
- 未公开的联系方式
- 内部会议链接
- 他人个人数据
