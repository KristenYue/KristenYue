# 岳玉婷 · Yuting Yue

### Systems Software · Verification Tooling · Simulation · Reliable AI Infrastructure

UCL 通信工程硕士、北京交通大学通信工程本科。使用 **C++/Python** 构建设备运行时、仿真验证工具、故障注入平台与可恢复 Agent Runtime，关注复杂软件在并发、重试、故障和版本演进中的可靠性。

`C++17` · `Python` · `Linux` · `CMake/CTest` · `pytest` · `FastAPI` · `PostgreSQL` · `Redis Streams` · `Docker` · `GitHub Actions`

## Engineering evidence

| 技术方向 | 项目证据 | 可执行结果 |
|---|---|---|
| **系统软件与设备验证** | [Edge Device Verification](https://github.com/KristenYue/edge-device-verification-lab) → [Smart Shelf](https://github.com/KristenYue/smart-supermarket-shelf) | C++17 状态机、有界并发、TCP/协议契约、故障注入；98 个验证场景、83.30% 覆盖率、50,000 条稳定性场景 |
| **AI Infra 与可靠性** | [Agent Runtime](https://github.com/KristenYue/agent-runtime-quality-platform) → [Telecom Incident Agent](https://github.com/KristenYue/telecom-network-incident-agent) | checkpoint、lease/fencing、幂等、Redis Streams、PostgreSQL；180/180 功能契约、70/70 故障处置 |
| **通信仿真与研发工具** | [FSO Coding Simulator](https://github.com/KristenYue/fso-coding-interleaving-simulator) | RS/LDPC、Gamma–Gamma、固定相干衰落、group-aware CI；14 个主实验与 12 个独立复现实验脚本 |

## Two review paths

- **系统软件 / 工具链：** [Edge Verification](https://github.com/KristenYue/edge-device-verification-lab) → [Smart Shelf](https://github.com/KristenYue/smart-supermarket-shelf) → [Runtime & Telecom](https://github.com/KristenYue/telecom-network-incident-agent)
- **AI 基础设施 / 可靠性：** [Agent Runtime](https://github.com/KristenYue/agent-runtime-quality-platform) → [Telecom Agent](https://github.com/KristenYue/telecom-network-incident-agent) → [Edge Verification](https://github.com/KristenYue/edge-device-verification-lab)

工程方法：**场景与风险建模 → 可执行契约 → 确定性故障注入 → Trace/指标 → 修复与回归 → CI 发布门禁**
