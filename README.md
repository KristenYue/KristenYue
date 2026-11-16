# 岳玉婷 · Yuting Yue

### Systems Software · R&D Tooling · Simulation & Verification · Reliable AI Infrastructure

UCL 通信工程硕士、北京交通大学通信工程本科。使用 **C++17 / Python / Linux** 构建设备运行时、仿真验证工具、故障注入平台与可恢复 Agent Runtime，将复杂系统的状态、并发、协议和故障行为转化为可复现、可度量、可持续回归的工程证据。

`C++17` · `Python` · `Linux` · `CMake/CTest` · `pytest` · `FastAPI` · `PostgreSQL` · `Redis Streams` · `Docker` · `GitHub Actions`

## Engineering evidence chain

```text
真实设备、通信与 Agent 场景
        ↓
C++ / Python 执行内核与状态模型
        ↓
协议契约、并发控制、超时重试与安全边界
        ↓
确定性故障注入、崩溃恢复与重复执行验证
        ↓
Trace、Coverage、机器可读报告与 Bad Cases
        ↓
Windows / Linux / Real-Service CI 发布门禁
```

## Quantified engineering evidence

| 工程能力 | 核心设计 | 可执行证据 |
|---|---|---|
| **C++ 系统与设备验证** | C++17 状态机、安全联锁、TCP 服务、有界线程池、背压与请求幂等 | **98 个自动化场景、83.30% 覆盖率**；Windows/Linux、Python 3.11/3.12 与 ASan/UBSan CI 通过 |
| **AIoT 设备可靠性** | 双设备状态融合、固定容量 Outbox、MQTT QoS 1、Telemetry v2、重启会话与乱序处理 | 固定随机种子验证 **50,000 条遥测**，覆盖重复、乱序、断网、未校时和设备重启 |
| **可恢复 Agent Runtime** | checkpoint、lease/heartbeat、fencing token、人工审批、幂等结果账本与统一 Trace | **180/180 功能契约、70/70 故障处置**；60 组重复提交的额外最终写入为 **0** |
| **真实异步服务链** | FastAPI、Redis Streams Consumer Group、PostgreSQL、异步 Worker、reclaim/ack/DLQ | 真实 Redis 崩溃接管、真实 PostgreSQL 双 Worker fencing 与六服务 Compose CI 全部通过 |
| **通信仿真与独立复现** | Gamma–Gamma、指向误差、固定相干衰落、率匹配 RS/LDPC、group-aware CI | **14 个主实验 + 12 个独立复现实验脚本**；确定性随机流、可中断续跑与独立实现自检 |

## Three connected proof chains

### 1. Systems software and device verification

[Edge Device Verification Lab](https://github.com/KristenYue/edge-device-verification-lab)
→ [Smart Shelf Edge-to-Cloud System](https://github.com/KristenYue/smart-supermarket-shelf)

从 C++ 设备状态机、TCP 服务、有界并发和安全联锁，延伸到双设备传感器融合、MQTT/TLS、离线缓存、端云协议和稳定性验证，形成：

```text
设备运行时 → 独立验证上位机 → 业务协议适配 → 故障回归 → 跨平台 CI
```

**岗位证据：** 系统软件、设备软件、研发工具链、嵌入式验证、工业软件。

### 2. Reliable AI infrastructure

[Agent Runtime & Evaluation Platform](https://github.com/KristenYue/agent-runtime-quality-platform)
→ [Telecom Network Incident Agent](https://github.com/KristenYue/telecom-network-incident-agent)

通用 Runtime 负责状态持久化、任务恢复、租约、fencing、幂等和 Trace；通信 Agent 负责 FastAPI、Redis Worker、领域工具、根因排序、安全验证和人工审批，形成：

```text
Agent Runtime → 异步任务调度 → 故障恢复 → 领域诊断 → 质量门禁
```

**岗位证据：** Agent 平台、AI Infra、Python 后端、可靠性工程、智能诊断平台。

### 3. Simulation and reproducible engineering

[FSO Coding & Interleaving Simulator](https://github.com/KristenYue/fso-coding-interleaving-simulator)

将通信理论转化为可运行的信道模型、编码实验、统计口径和独立复现流程，控制码率、信道相干长度、交织深度和随机性，形成：

```text
模型假设 → 组件验证 → Monte Carlo 实验 → 统计分析 → 独立复现
```

**岗位证据：** 仿真平台、科学计算、通信软件、算法验证、专业研发工具。

## Role alignment

| 目标岗位 | 直接技术证据 |
|---|---|
| **系统软件 / 研发工具链** | C++17、Linux、状态机、有界并发、TCP、CMake、Sanitizer、跨平台 CI |
| **仿真验证 / 测试开发** | 故障注入、协议契约、随机性管理、Coverage、Bad Case、机器可读报告 |
| **AI 基础设施 / Agent 平台** | Runtime、异步 Worker、PostgreSQL、Redis Streams、租约接管、幂等与 Trace |
| **设备软件 / 工业软件** | 安全联锁、Telemetry、MQTT/TLS、Outbox、设备重启和端云一致性 |

## Engineering method

```text
风险与场景建模
    → 可执行契约
    → 确定性故障注入
    → Trace、Coverage 与指标
    → 缺陷修复
    → 回归测试
    → CI 发布门禁
```

我关注的不只是功能是否运行，还包括：

- 故障发生后能否恢复到明确状态；
- 重试和重复提交是否产生额外副作用；
- 并发和过载是否有清晰边界；
- 测试结果能否被独立复现；
- 版本升级是否有机器可执行的质量门禁。

## Supporting engineering evidence

- [Public Opinion Agent](https://github.com/KristenYue/public-opinion-agent-eval)：事件级数据隔离、Hybrid RAG、人工复核、异步任务与审计 Trace。
- [FSO Agent Runtime Benchmark](https://github.com/KristenYue/fso-agent-runtime-benchmark)：冻结任务、跨 Runtime 对照、轨迹级评测与独立评分。
- [Agent Reliability Eval](https://github.com/KristenYue/agent-reliability-eval)：Agent 轨迹匹配、成对回归分析和可配置质量门禁。
- [Valorant Core QA](https://github.com/KristenYue/valorant-core-qa)：状态机、事务幂等、弱网故障注入、断线重连与日志分析。

## Suggested review paths

- **系统软件 / 研发工具链：** [Edge Verification](https://github.com/KristenYue/edge-device-verification-lab) → [Smart Shelf](https://github.com/KristenYue/smart-supermarket-shelf) → [Agent Runtime](https://github.com/KristenYue/agent-runtime-quality-platform)
- **AI Infra / Agent 平台：** [Agent Runtime](https://github.com/KristenYue/agent-runtime-quality-platform) → [Telecom Agent](https://github.com/KristenYue/telecom-network-incident-agent) → [Edge Verification](https://github.com/KristenYue/edge-device-verification-lab)
- **仿真验证 / 通信软件：** [FSO Simulator](https://github.com/KristenYue/fso-coding-interleaving-simulator) → [Edge Verification](https://github.com/KristenYue/edge-device-verification-lab)
- **AI 评测与应用：** [Public Opinion Agent](https://github.com/KristenYue/public-opinion-agent-eval) → [Agent Runtime](https://github.com/KristenYue/agent-runtime-quality-platform)

## Current focus

继续强化 **C++ 并发与性能、分布式任务恢复、Agent Runtime、可观测性、确定性回放和可执行质量门禁**，面向系统软件、研发工具链、仿真验证与 AI 平台工程岗位。
