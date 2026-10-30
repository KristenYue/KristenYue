# 岳玉婷 | Yuting Yue

> AI软件测试 / LLM & Agent Evaluation / AI Reliability  
> Python · pytest｜模型评估｜故障注入｜自动化回归｜质量门禁

## 关于我 About Me

UCL通信工程硕士，求职方向为**AI软件测试、AI可靠性、LLM/Agent评测和测试开发**。

关注AI系统的可测性、稳定性、可追溯性与发布质量，具备以下实践：

- 🤖 LLM/Agent工作流契约测试与轨迹验证
- 💥 超时、429、5xx、坏JSON等故障注入与恢复验证
- 📊 Accuracy、Macro-F1、Recall等模型指标评估
- 🔍 Bad Case分析、数据泄漏防控与回归集建设
- 🧪 Python/pytest自动化测试与GitHub Actions质量门禁
- 📝 JSONL日志、工具调用轨迹和运行审计分析

## 精选项目 Featured Projects

### 🤖 AI Agent可靠性测试与故障恢复

面向工具调用型AI Agent构建可靠性评估框架，重点验证工作流契约、异常恢复、工具轨迹和版本发布质量。

- 设计8类workflow contract
- 在36个Agent任务上执行288项自动化检查
- 覆盖输出一致性、轨迹顺序、证据溯源和降级状态
- 注入超时、429、5xx、坏JSON等7类故障
- 验证重试、降级和人工接管路径，7/7按预期恢复
- 开发run audit CLI，输出轨迹、错误、风险标记和评估结果
- 52项工程测试全部通过，并形成发布前回归门禁

[查看项目 View Project](https://github.com/KristenYue/agent-reliability-eval)

---

### 📊 AI模型测试与风险复核

在本科毕设情感分析系统基础上重构模型评估链路，重点处理数据泄漏、类别不均衡、负面样本漏检和高置信误判。

- 统一XGBoost与中文RoBERTa推理输出
- 建立Accuracy、Macro-F1、Negative Recall多指标评估
- 按事件切分169/35/38条样本，避免同事件数据泄漏
- 对107条高风险样本二次复核并修正24条标签
- Negative Recall由3.6%提升至60.7%
- 将高置信误判和负面漏检转化为Bad Case回归规则

[查看项目 View Project](https://github.com/KristenYue/public-opinion-agent-eval)

---

### 🧪 竞技软件核心模块测试与自动化

以竞技游戏公开流程为业务背景，验证状态机、数值边界、接口契约、请求幂等、弱网和日志分析能力。

- 使用Python/pytest构建122个参数化自动化场景
- 覆盖状态迁移、数值边界、重复请求和服务端一致性
- 模拟延迟、丢包、重复包和乱序
- 使用10万条模拟事件验证流式日志分析
- 配置GitHub Actions自动化回归

[查看项目 View Project](https://github.com/KristenYue/valorant-core-qa)

## 能力方向 Focus Areas

### AI系统测试

`LLM Evaluation` `Agent Evaluation` `Workflow Contract`  
`Failure Injection` `Recovery Testing` `Trajectory Validation`

### 模型评估

`Accuracy` `Macro-F1` `Precision` `Recall`  
`Bad Case Analysis` `Data Leakage` `Class Imbalance`

### 测试工程

`Python` `pytest` `Requests` `Postman`  
`GitHub Actions` `JSON/JSONL` `Docker` `Linux`

## 当前关注 Currently Exploring

- LLM非确定性输出的稳定性与回归测试
- RAG检索、生成和引用链路的分层评估
- Agent工具调用轨迹与工作流契约测试
- Prompt注入、越权调用和异常输入测试
- AI系统评测集、Bad Case和发布门禁建设

## 联系方式 Contact

- GitHub: [KristenYue](https://github.com/KristenYue)
- Email: yueyt1112@163.com
