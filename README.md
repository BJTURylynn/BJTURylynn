<div align="center">

<img src="https://raw.githubusercontent.com/BJTURylynn/BJTURylynn/main/assets/profile-header-v2.png" width="100%" alt="Rylynn：AI Agents、Embedded Systems、Communication Engineering" />

**AI Agent · 嵌入式与边缘系统 · 通信工程**

北京交通大学 · 通信工程硕士在读

[关于我](#about) · [精选项目](#projects) · [研究与竞赛](#research) · [项目技术](#toolbox) · [交流与合作](#connect)

</div>

<a id="about"></a>

## 关于我

我是 **Rylynn**，北京交通大学通信工程硕士在读，本科毕业于安徽大学电子信息工程专业。目前关注 **AI Agent、大模型应用与嵌入式边缘系统**，尝试把业务数据、工具调用和工程验证连接起来。

- **应用开发**：围绕实际问题组织工具、数据和交互，让分析结果能够追溯到来源。
- **边缘实践**：探索 ESP32 与 Linux 之间的数据传输、应用层任务调度和只读运行解释。
- **做项目的方式**：先跑通流程，再记录实验、检查边界，保留可复现的代码与结果。

<a id="projects"></a>

## 精选项目

### 01 / SupplyLens Agent

**采购到货异常分析助手：查订单、核对异常、检索 SOP，生成带证据的报告。**

使用 LangGraph 编排订单快照、异常计算和 SOP 检索三类工具，由 Python 规则计算业务事实，模型结合工具结果组织回答。支持自然语言查询、多轮跟进、Excel/CSV 导入及报告下载。

`业务快照 → 异常计算 → SOP 检索 → 引用校验 → 分析报告`

- **数据与交互**：支持六类业务表的字段映射、预览校验和事务写入，区分已确认异常与信息缺口。
- **工程验证**：通过 **186 项离线测试、30 个固定 Demo 案例**；完成真实 MySQL 接入及 SQLite → MySQL 逐行校验迁移。
- **模型联调**：GLM 对模拟订单完成单例工具调用，保留报告、业务证据及调用轨迹。

<sub>当前使用模拟业务资料验证；固定 Demo 验收与真实模型单例联调分别记录。</sub>

<sub>Python · LangGraph · FastAPI · Streamlit · SQLAlchemy · SQLite / MySQL · pytest</sub>

**[查看仓库 →](https://github.com/BJTURylynn/supplylens-agent)** · [演示与截图](https://github.com/BJTURylynn/supplylens-agent#演示) · [验证记录](https://github.com/BJTURylynn/supplylens-agent/blob/main/docs/validation.md)

---

### 02 / ESP32 × Linux Edge Scheduler

**把数据接收、任务调度与运行解释连接成可复现的边缘处理链。**

基于 ESP-IDF 与 Linux C11 / POSIX，采用 TCP / NDJSON、有界队列和单工作线程，实现 FIFO / 非抢占优先级调度、滑动平均与 RMS 计算，并记录逐任务运行日志。

`合成数据 → TCP / NDJSON → 任务队列 → 调度与计算 → 日志与报告`

- **工程实现**：完成 ESP32 固件构建、真实 C 服务集成测试与 ASan / UBSan 检查。
- **对照实验**：使用相同合成负载，两种策略各重复三轮，共完成 **192 个任务、零拒绝**，比较紧急与普通任务的等待时间和策略取舍。
- **只读解释**：通过状态查询、报告读取两个固定工具，基于运行数据与规则解释调度结果。

<sub>当前完成本机集成与固件构建；公开版本的助手基于规则，真实接板与无线链路待验证。</sub>

<sub>C11 · ESP32 / ESP-IDF · Linux / POSIX · TCP / NDJSON · Python</sub>

**[查看仓库 →](https://github.com/BJTURylynn/esp32-linux-edge-scheduler)** · [验证记录](https://github.com/BJTURylynn/esp32-linux-edge-scheduler/blob/main/docs/validation.md) · [协议设计](https://github.com/BJTURylynn/esp32-linux-edge-scheduler/blob/main/docs/protocol.md)

<a id="research"></a>

## 研究与竞赛背景

- **复杂场景下多模态情感预测的数学建模与算法设计**：研究生数学建模竞赛团队项目，涉及文本、语音、视觉特征对齐、融合预测、缺失鲁棒性与可解释分析。
- **低剖面超表面圆极化天线设计**：本科毕业设计，使用 HFSS 完成结构优化与全波仿真，分析阻抗、轴比、增益及表面电流。

## 正在规划

**[车联网诊断 Agent 模拟台架](https://github.com/BJTURylynn/iov-edge-agent-lab)**：围绕 ESP32、Pico、Arduino 与 Windows 模拟链路，规划串口、MQTT、缓存与只读诊断流程。当前仅完成方案设计与文档归档，尚未实施。

<a id="toolbox"></a>

## 项目中使用的技术

| 方向 | 技术与实践 |
| :--- | :--- |
| 编程与数值计算 | Python、C、MATLAB |
| Agent 与应用 | LangGraph、FastAPI、Streamlit、工具调用、SOP 检索与引用校验 |
| 边缘系统与通信 | ESP32 / ESP-IDF、Linux / POSIX、TCP / NDJSON、应用层任务队列 |
| 数据与验证 | SQLAlchemy、SQLite / MySQL、pytest、运行日志与可复现实验 |
| 仿真与分析 | HFSS、Origin、信号处理与通信建模 |

<a id="connect"></a>

## 交流与合作

欢迎交流 **AI Agent、大模型应用、嵌入式软件与车联网**方向的实习机会。

项目复现、问题反馈或合作想法，可以在对应仓库发起 Issue。

<div align="center">

**[浏览我的 GitHub 仓库 →](https://github.com/BJTURylynn?tab=repositories)**

<sub>用项目连接 AI 与边缘设备。</sub>

</div>
