# 岳玉婷 / Yuting Yue

### 系统软件 · 研发工具链 · 仿真验证 · 可靠 AI 基础设施

伦敦大学学院（UCL）通信工程硕士，北京交通大学通信工程本科。  
主要使用 **C++、Python 和 Linux**，关注设备软件与 AI 系统中的并发执行、故障恢复、自动化验证和工程可观测性。

项目围绕同一个工程问题展开：

> **如何把存在并发、通信、状态和故障恢复问题的复杂系统，转化为可复现、可验证、可诊断的工程系统。**

---

## 核心工程结果

| 工程问题 | 量化结果 | 技术能力 |
|---|---:|---|
| 边缘设备软件如何进行自动化回归验证 | **98 项回归测试，83.30% 测试覆盖率** | C++/Python 联合开发、测试编排、持续集成 |
| 多设备并发与异常场景如何稳定复现 | 支持并发调度、超时、重试、有界队列和故障注入 | 并发控制、异常处理、确定性测试 |
| IoT 端云链路能否持续稳定运行 | 固定随机种子完成 **50,000 条遥测消息**稳定性实验 | 状态机、MQTT/TLS、遥测协议、端云协同 |
| Agent 异常后能否恢复且避免重复提交 | **180/180** 功能场景通过；**70/70** 故障场景受控处理 | Checkpoint、租约、心跳、Fencing、幂等控制 |
| 重复执行是否会污染最终结果 | **60 组重复任务，额外最终写入为 0** | Exactly-once 效果、并发一致性、结果提交保护 |
| 故障恢复是否区分“恢复”和“安全失败” | 70 个故障场景中 **68 个恢复、2 个 Fail-closed** | 故障分类、安全降级、可解释验收 |
| 真实中间件故障能否进入持续集成 | Redis、PostgreSQL、Docker Compose 集成测试进入 CI | 后端可靠性、服务接管、工程质量门禁 |
| 通信算法实验能否被独立复现 | **14 个主实验脚本 + 12 个独立复现实验脚本** | 通信仿真、实验设计、结果复现 |

---

# 三条项目证据链

## 1. 设备软件、仿真验证与研发工具链

### [C++/Python 边缘设备仿真与验证平台](https://github.com/KristenYue/edge-device-verification-lab)

面向设备控制软件在真实硬件接入前难以稳定复现并发、超时和异常状态的问题，构建设备仿真与自动化验证平台。

**核心设计**

- 使用 C++17 实现设备状态与并发执行模型。
- 使用 Python 实现测试编排、契约验证、故障注入和报告生成。
- 支持超时、重试、断连、有界队列和异常响应等故障场景。
- 使用 pytest 建立接口、状态转换和回归测试。
- 在 GitHub Actions 中执行 Windows/Linux、Python 3.11/3.12 跨平台验证。
- 使用 AddressSanitizer 和 UndefinedBehaviorSanitizer 检查内存与未定义行为问题。

**工程结果**

- 建立 **98 项自动化回归测试**。
- 当前测试覆盖率达到 **83.30%**。
- 将设备异常从偶发问题转化为可重复执行的测试用例。
- 形成“设备模型—故障注入—自动断言—回归报告”的完整验证闭环。

---

### [AIoT 智能货架与设备可靠性验证](https://github.com/KristenYue/smart-supermarket-shelf)

面向智能零售中的传感器采集、库存状态转换和端云通信场景，验证嵌入式设备状态与遥测链路的稳定性。

**核心设计**

- 使用 C++17 实现设备端状态机、传感器数据处理和库存状态转换。
- 设计 Telemetry v2 遥测数据契约，统一设备端与云端消息结构。
- 使用 MQTT/TLS 和 AWS IoT 构建设备到云端的通信链路。
- 使用 Java 云服务处理设备消息、库存事件和异常状态。
- 使用固定随机种子生成可重复的长时间遥测实验。

**工程结果**

- 完成 **50,000 条遥测消息**稳定性实验。
- 覆盖设备在线、库存变化、传感器异常和通信故障场景。
- 验证状态机、数据契约和端云链路在持续输入下的一致性。

### 整体项目逻辑

```text
C++ 设备建模
    ↓
进程、线程与并发控制
    ↓
故障注入与确定性复现
    ↓
Python 自动化验证
    ↓
跨平台 CI 与质量门禁
```

---

## 2. Agent Runtime、故障恢复与 AI 基础设施

### [可靠 Agent Runtime 与质量门禁平台](https://github.com/KristenYue/agent-runtime-quality-platform)

面向 Agent 长任务执行过程中可能出现的进程崩溃、任务重复领取、工具重复调用和结果重复提交问题，构建可恢复、可追踪、可验收的任务执行平台。

**核心设计**

- 使用 Checkpoint 保存任务执行进度，支持异常后继续执行。
- 使用 Lease 和 Heartbeat 检测失效 Worker。
- 使用 Fencing Token 阻止旧 Worker 恢复后覆盖新结果。
- 使用幂等键保护工具调用和最终结果提交。
- 使用 Trace 记录任务状态、工具调用、重试和恢复过程。
- 将功能正确性、故障恢复和重复执行控制转化为自动化质量门禁。

**工程结果**

- **180/180** 项功能验收场景通过。
- **70/70** 项故障处理场景进入受控结果。
- 其中 **68 项自动恢复，2 项安全失败（Fail-closed）**。
- 完成 **60 组重复任务实验**，额外最终写入为 **0**。
- 验证任务在崩溃、超时、重复领取和旧 Worker 恢复场景下的结果一致性。

---

### [通信网络故障诊断与可靠任务执行平台](https://github.com/KristenYue/telecom-network-incident-agent)

将 Agent Runtime 的可靠性机制应用到通信网络故障诊断场景，验证真实 Redis、PostgreSQL 和多 Worker 环境下的任务接管与消息处理。

**核心设计**

- 使用 Redis Streams Consumer Group 实现故障任务分发。
- 使用 Pending 消息回收处理 Worker 异常退出后的任务接管。
- 使用 Ack、重试和死信队列管理失败消息。
- 使用 PostgreSQL Lease 与 Fencing 控制任务所有权。
- 使用 FastAPI 提供任务接口，Worker 执行诊断流程。
- 使用 Docker Compose 启动真实依赖服务并执行集成测试。
- 在 GitHub Actions 中运行服务启动、接管、消息恢复和可靠性门禁。

**工程结果**

- Redis 消息可靠性测试进入自动化 CI。
- PostgreSQL Worker 接管和 Fencing 测试进入自动化 CI。
- Docker Compose 真实服务冒烟测试进入自动化 CI。
- 形成“任务进入—Worker 执行—故障发生—任务接管—结果验证”的完整链路。

### 整体项目逻辑

```text
异步任务执行
    ↓
Checkpoint 与状态持久化
    ↓
Lease、Heartbeat 与任务接管
    ↓
Fencing 与幂等提交
    ↓
Trace、故障诊断与质量门禁
```
---

## 3. 通信仿真、算法验证与实验复现

### [FSO 编码与交织仿真平台](https://github.com/KristenYue/fso-coding-interleaving-simulator)

面向自由空间光通信中湍流信道、信道编码和交织策略的对比问题，构建可重复执行的通信算法仿真实验。

**核心设计**

- 建立 FSO 湍流信道与误码性能仿真流程。
- 对比 RS、LDPC 和交织策略在不同信道条件下的表现。
- 将参数、随机种子和实验入口显式化，降低实验复现成本。
- 将主实验与独立复现实验分离，避免只依赖单次运行结果。
- 使用 CI 检查代码结构、依赖和基础可执行性。

**工程结果**

- 整理 **14 个主实验脚本**。
- 建立 **12 个独立复现实验脚本**。
- 将硕士研究中的仿真代码整理为可阅读、可运行、可验证的工程仓库。

### 整体项目逻辑

```text
通信系统建模
    ↓
信道与编码算法仿真
    ↓
实验参数控制
    ↓
结果对比与独立复现
    ↓
研究代码工程化
```

---

# 补充：AI 测试与评测能力

### [中文舆情 Agent 评测平台](https://github.com/KristenYue/public-opinion-agent-eval)

该项目完成：

- 任务完成与工具调用评测
- 证据追踪和结构化报告
- 人工复核流程
- Bad Case 分类与回归
- 模型输出质量与安全边界测试

我不仅能够实现 Agent 执行系统，也能够从测试、验收和风险控制角度评价 AI 系统。

---

# 技术能力矩阵

| 能力方向 | 技术与工程实践 | 对应项目证据 |
|---|---|---|
| 系统开发 | C++17、Python、Linux、进程、线程、IPC、状态机 | 边缘设备验证平台、智能货架 |
| 并发与可靠性 | 有界队列、超时、重试、租约、心跳、Fencing、幂等 | 边缘设备验证平台、Agent Runtime |
| 后端与中间件 | FastAPI、PostgreSQL、Redis Streams、Docker Compose | 通信故障诊断平台 |
| 设备与端云通信 | MQTT/TLS、AWS IoT、遥测协议、传感器状态 | 智能货架 |
| 测试与验证 | pytest、契约测试、故障注入、回归测试、Bad Case 分析 | 全部核心项目 |
| 调试与质量 | GDB、Sanitizer、结构化日志、Trace、GitHub Actions | 边缘设备验证平台、Agent Runtime |
| 通信仿真 | FSO、RS、LDPC、交织、误码性能实验 | FSO 仿真平台 |
| AI 工程化 | Agent Runtime、工具调用、任务恢复、质量门禁、评测 | Runtime、通信故障诊断、舆情评测 |

---

# 我的工程方法

我的项目通常按照以下方式推进：

1. 将业务场景抽象为明确的状态、事件和系统边界。
2. 定义正常路径、异常路径和可验证的验收条件。
3. 通过固定随机种子、故障注入或真实中间件复现问题。
4. 使用结构化日志和 Trace 保留执行证据。
5. 将 Bad Case 固化为自动化回归测试。
6. 使用 CI 持续执行测试、集成验证和质量门禁。
7. 使用量化结果判断系统是否真正达到验收标准。

我关注的不只是“功能能够运行”，还包括：

- 异常发生后能否恢复；
- 重复执行是否会产生重复结果；
- 多 Worker 是否会发生所有权冲突；
- 设备状态和云端状态是否一致；
- 问题能否被稳定复现；
- 修复能否沉淀为长期回归测试。

---

# 推荐阅读路径

如果你关注 **系统软件、C++、研发工具链和仿真验证**：

1. [C++/Python 边缘设备仿真与验证平台](https://github.com/KristenYue/edge-device-verification-lab)
2. [AIoT 智能货架与设备可靠性验证](https://github.com/KristenYue/smart-supermarket-shelf)
3. [FSO 编码与交织仿真平台](https://github.com/KristenYue/fso-coding-interleaving-simulator)

如果你关注 **Agent 平台、AI 基础设施和后端可靠性**：

1. [可靠 Agent Runtime 与质量门禁平台](https://github.com/KristenYue/agent-runtime-quality-platform)
2. [通信网络故障诊断与可靠任务执行平台](https://github.com/KristenYue/telecom-network-incident-agent)
3. [C++/Python 边缘设备仿真与验证平台](https://github.com/KristenYue/edge-device-verification-lab)

如果你关注 **测试开发、质量工程和 AI 评测**：

1. [C++/Python 边缘设备仿真与验证平台](https://github.com/KristenYue/edge-device-verification-lab)
2. [可靠 Agent Runtime 与质量门禁平台](https://github.com/KristenYue/agent-runtime-quality-platform)
3. [中文舆情 Agent 评测平台](https://github.com/KristenYue/public-opinion-agent-eval)

---

## 当前关注方向

- Agent Runtime 与可靠任务执行
- AI 系统可观测性与质量门禁
- C++/Python 仿真验证工具链
- 故障注入、恢复验证与性能测试
- 设备软件和 AI 系统的工程可靠性

📍 求职方向：系统软件｜研发工具链｜仿真验证｜Agent 平台与 AI 基础设施
