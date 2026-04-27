# XClaw Agent OS: 企业级智能体操作系统

**XClaw Agent OS** 是一个让企业可以像调用 API 一样调用 AI Agent 的操作系统平台（Agent OS + AI PaaS）。

它不仅是一个 AI 工具，更是解决当前 AI 落地“不可控（缺少治理）、不可执行（停留在对话层）、不可商业化（缺少计费交付）”三大痛点的完整闭环全栈方案。

---

## 🌟 核心特性

*   **多 Agent 协同矩阵**：由祝欣儿（主控）、小梦（创作）、老周（研发）、运维小王（运维）构成的专家集群，实现复杂任务的并行处理与深度分工。
*   **M0-M4 深度记忆系统**：从原始事件（M0）到权威事实（M1）再到长期经验（M2），构建具备自我增长、可回滚、可审计的 AI 大脑。
*   **XBIS 稳定业务层**：提供一层稳定、可治理、可审计的业务接入层，支持异步任务、同步轻任务及人工复核模式。
*   **AI 驱动工程 SOP**：内置严密的 Phase Gates（阶段闸门）和自检循环，确保生成的代码与交付物符合工程级标准 [SOP, 39]。
*   **自动化自恢复**：内置 Watchdog（看门狗）监控，确保 Gateway、存储和消息主链的 7x24 小时高可用。

---

## 🏗️ 架构概览

XClaw 采用三层驱动结构，实现从生产到变现的闭环：

1.  **Agent OS (内核层)**：负责多 Agent 调度、RabbitMQ 消息主链、PromptX 记忆主存及 Authority 规范事实层。
2.  **XBIS (平台层)**：企业级 AI 接入中台。处理 API 鉴权、任务落库、审计日志、回调机制及人工复核逻辑。
3.  **API Marketplace (商业层)**：提供 API Key 管理、计费统计、套餐系统及能力市场，支持 AI 能力的商业化交付。

---

## 🧠 记忆治理体系

XClaw 将记忆分为五个层级，确保 AI 的行为既灵活又遵循规范：

| 层级 | 名称 | 说明 |
| :--- | :--- | :--- |
| **M0** | 事件账本 | 记录所有原始事件、日志与上下文。 |
| **M1** | Authority 规范层 | 存储当前可信事实、版本、冲突处理及人工复核状态。 |
| **M2** | PromptX 长期层 | 存储角色人格、经验方法论及长期关系特征。 |
| **M3** | 前意识工作集 | 任务相关的投影、召回摘要与注意中心。 |
| **M4** | 会话运行时 | 临时的对话与短期上下文。 |

---

## 🛠️ 快速开始

### 环境依赖
*   **OS**: Windows 11 / Linux (Docker)
*   **Languages**: Python 3.13+, PowerShell 7.5+
*   **Infrastructure**: RabbitMQ (Docker), Redis, vLLM (OpenAI-compatible)

### 部署步骤
1.  **克隆仓库**
    ```bash
    git clone https://github.com/your-repo/xclaw.git
    cd xclaw
    ```
2.  **配置环境**
    参考 `xbis/.env` 模板配置文件，设置 PostgreSQL、Redis 及 RabbitMQ 访问凭据。
3.  **启动服务**
    使用 OpenClaw 生命周期托管脚本一键启动：
    ```powershell
    .\OpenClaw-Gateway.cmd start
    ```
4.  **真实验证**
    运行健康检查流以确保全链路（API -> MQ -> Agent -> RPC）通畅：
    ```powershell
    python xbis/scripts/validate_healthcheck_flows.py
    ```

---

## 🔌 API 接入 (XBIS)

XBIS 提供标准的 RESTful API 接口，支持三种核心调用模式：

*   **异步模式 (Async)**：适用于长耗时任务，支持审计链与结果回写。
*   **同步轻模式 (Sync)**：适用于低风险、短时任务。
*   **人工复核模式 (Review)**：高风险操作需经过 [人工复核中心](http://127.0.0.1:8787) 确认后方可执行。

```http
POST /api/v1/invocations/sync
Content-Type: application/json
X-API-Key: <YOUR_API_KEY>

{
  "agent": "assistant",
  "skill": "healthcheck",
  "payload": { "question": "检查当前服务器运行状态" }
}
```

---

## 📈 路线图 (Roadmap)

*   **阶段 1 (当前)**: 完善 XBIS 平台，打磨 AIOps（运维助手）与研发助手场景。
*   **阶段 2 (融资后)**: 推出企业版 SaaS，建立计费模型与多租户隔离体系。
*   **阶段 3 (生态化)**: 开放能力市场，引入第三方开发者，建立 Agent 行业标准生态。

---

## ⚖️ 许可与贡献

本项目采用 [Apache License 2.0](LICENSE) 许可。

欢迎通过 Issue 提交建议或 PR 贡献代码。在提交代码前，请确保符合本项目的 **AI 驱动开发 SOP**，包括通过 Phase Gates 评审与组件分层规范 [SOP, 39]。

---

**XClaw: 打造可以信任、可以执行、可以增长的 AI 伙伴。**
