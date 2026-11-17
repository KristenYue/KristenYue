# 岳玉婷 / Yuting Yue

**工业 AI 应用 · Agent Runtime · 设备系统软件**

UCL 通信工程硕士，北京交通大学通信工程本科。曾在中国电信物联网研发部参与 CTWing/AEP 设备管理后端与端云联调。主要使用 Python、C++17 和 Linux，关注工业设备诊断、任务编排与设备通信软件开发。

## 核心项目

| 项目 | 实现的研发能力 | 可核查结果 |
| --- | --- | --- |
| [工业设备诊断与任务编排](https://github.com/KristenYue/telecom-network-incident-agent) | FastAPI 接单、持久化任务、Worker、工具白名单、版本化知识检索 | 本机通过 HTTP、SQLite 和 TCP 串联仿真设备。正常执行、急停联锁和离线诊断均有[原始轨迹](https://github.com/KristenYue/telecom-network-incident-agent/blob/main/docs/device-api-smoke.jsonl)。 |
| [C++ 设备运行时与控制](https://github.com/KristenYue/edge-device-verification-lab) | C++17 状态机、TCP/JSON Lines、Socket RAII、有界并发与命令幂等 | [4,200 次对照请求全部成功](https://github.com/KristenYue/edge-device-verification-lab/blob/main/benchmarks/windows-baseline-comparison.json)，新版吞吐中位数未提升。慢连接场景复现排队超期拒绝。 |
| [双节点 AIoT 智能货架](https://github.com/KristenYue/smart-supermarket-shelf) | 设备端状态判定、MQTT/TLS、AWS IoT、Java 服务与遥测一致性 | [50,000 条参考网关合成输入](https://github.com/KristenYue/smart-supermarket-shelf/blob/main/iot-test-harness/tools/run_stability.py)中，接收 48,512 条，识别 1,012 条重复、13 条乱序和 463 条载荷冲突。 |

## 从这里进入

- **AI 应用与诊断平台**　[工业 Agent 架构与复现](https://github.com/KristenYue/telecom-network-incident-agent/blob/main/docs/INDUSTRIAL_AGENT.md) · [共享 Agent Runtime](https://github.com/KristenYue/agent-runtime-quality-platform)
- **设备软件与研发工具**　[C++ 连接队列、幂等与超时](https://github.com/KristenYue/edge-device-verification-lab/blob/main/docs/RUNTIME_HARDENING.md)
- **IoT 与通信**　[双节点固件、MQTT/TLS 和配置版本](https://github.com/KristenYue/smart-supermarket-shelf/blob/main/docs/FIRMWARE_VALIDATION.md) · [自由空间光通信编码与交织仿真](https://github.com/KristenYue/fso-coding-interleaving-simulator)

当前设备诊断演示使用仿真设备和确定性编排。真实模型调用、分布式部署与目标环境验收进度见各项目的工程说明。
