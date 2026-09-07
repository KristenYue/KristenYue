# 岳玉婷 | AI Agent 工程与评测

**AI Agent / 大模型应用开发 · Agent Runtime · RAG · Evaluation**

伦敦大学学院（UCL）通信工程硕士，北京交通大学通信工程本科，预计 **2026 年 12 月毕业**。

专注于 AI Agent 系统的工程实现与可靠性评测，具备从业务任务建模、Agent 工作流与工具调用开发，到冻结评测、故障注入、自动化测试和实验分析的完整项目经验。

**求职方向：AI Agent / 大模型应用开发 / Agent 评测与可靠性**

## 核心能力

- **Agent 工程：** LangGraph、自研 Agent Runtime、Tool Calling、状态管理、错误恢复
- **大模型应用：** RAG、Prompt Engineering、结构化输出、中文 NLP、业务工作流
- **评测与可靠性：** 冻结任务、轨迹对齐、故障注入、结果契约、可复现实验
- **工程实践：** Python、Pytest、Git、GitHub Actions、Gradio、自动化测试

## 代表项目

### 1. [FSO Agent Runtime Benchmark](https://github.com/KristenYue/fso-agent-runtime-benchmark)

**预注册对比 LangGraph 与自研轻量 Agent Runtime，验证不同 Agent 架构在相同条件下的行为一致性与运行开销。**

- 独立实现不依赖 LangGraph、LangChain Core 的轻量 Agent Runtime
- 冻结任务、工具、模型参数与预算，完成公平可复现的对照实验
- LangGraph 与自研 Runtime 均完成 `24/24` 个 Challenge 任务
- 两侧均产生 `112` 次工具调用，并对齐终止状态、最终配置与工具轨迹
- 提示词 Token 数保持一致，总 Token 差异仅为 `20`
- 完成 `500` 轮离线配对实验：自研 Runtime 中位调度开销 `0.295 ms`，LangGraph 基线为 `6.210 ms`
- 建立 `125` 项自动化测试，GitHub Actions 覆盖 Python 3.11 和 3.12
- 保存预注册方案、冻结数据、原始运行记录和实验报告，支持结果复核

`Python` · `Agent Runtime` · `LangGraph` · `Tool Calling` · `Evaluation` · `Pytest`

---

### 2. [Public Opinion Agent Evaluation](https://github.com/KristenYue/public-opinion-agent-eval)

**面向中文互联网舆情研判场景，构建包含信息处理、风险分析和结构化报告生成的 Agent 应用。**

- 将舆情分析任务拆分为可执行的 Agent 工作流
- 实现检索增强、工具调用、证据整理和结构化输出
- 强调分析结论与来源证据之间的可追溯性
- 建立评测数据、失败案例与结果分析流程
- 提供可交互的在线演示入口，展示完整业务链路

`LLM Agent` · `RAG` · `Tool Calling` · `Structured Output` · `Gradio`

---

### 3. [Agent Reliability Evaluation](https://github.com/KristenYue/agent-reliability-eval)

**针对工具调用型 Agent 建立可靠性评测体系，验证 Agent 在异常输入和工具故障下的行为。**

- 设计工具错误、无效输入、不可行配置等故障场景
- 检查终止状态、最终回答、工具轨迹与预期契约是否一致
- 评估 Agent 的错误识别、任务拒绝和故障恢复能力
- 保存结构化评测数据与可复现实验结果
- 通过自动化测试防止数据、契约和结果意外漂移

`Agent Evaluation` · `Failure Recovery` · `Tool Calling` · `Pytest`

---

### 4. [Chinese Sentiment Analysis Thesis](https://github.com/KristenYue/chinese-sentiment-analysis-thesis)

**面向中文社交媒体评论的情感分析研究，本科毕业设计获北京市优秀本科毕业设计（论文）。**

- 完成中文社交媒体文本清洗、特征处理、建模与实验分析
- 对比不同情感分析方法的表现并分析模型误差
- 整理代码、实验结果和论文材料，形成可复现项目

`NLP` · `Sentiment Analysis` · `Machine Learning` · `Python`

## 教育与经历

### University College London（UCL）

**MSc Communication Engineering｜通信工程硕士**  
2025.09 – 2026.12

### 北京交通大学

**通信工程本科**  
2021.09 – 2025.06

- 本科毕业设计：社交媒体评论情感分析研究
- 获北京市优秀本科毕业设计（论文）

### 中国电信

**软件开发实习生**  
2024.06 – 2024.08

- 参与 Python 自动化工具开发
- 完成数据处理、文件处理与业务流程自动化相关工作
- 参与需求沟通、功能实现和测试交付

## 我的工程方法

我关注的不只是 Agent 能否在一次演示中完成任务，还关注：

- 任务、工具和成功条件是否定义清楚
- 不同方案之间的对比是否公平
- 工具调用与状态变化是否可以追踪
- Agent 遇到错误后能否安全恢复或正确拒绝
- 结果能否通过自动化测试和冻结数据验证
- 项目是否具有清晰文档并能够被其他人复现

## Contact

- GitHub：[KristenYue](https://github.com/KristenYue)
- Email：`yueyt1112@163.com`
- 求职方向：**AI Agent / 大模型应用开发 / Agent 评测与可靠性**


欢迎交流 AI Agent 工程、Agent Runtime、RAG 与大模型评测。
