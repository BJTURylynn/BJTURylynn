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
- **边缘实践**：实现 ESP32-C3 / Arduino 板端计算、Linux 中央任务派发和只读运维解释。
- **做项目的方式**：先跑通流程，再记录实验、检查边界，保留可复现的代码与结果。

<a id="projects"></a>

## 精选项目

### 01 / EdgeScope · 双设备边缘计算与运维 Agent

**网页提交任务，Linux 中央调度，ESP32-C3 与 Arduino 板上计算，再用 Agent 核对和解释实验结果。**

第二版将两块开发板升级为计算节点：Linux C 中央派发器通过非阻塞 socket / poll 管理有界队列和设备会话，ESP32-C3 通过 Wi-Fi/TCP、Arduino Uno 通过 USB 串口接收任务，实际执行滑动平均、均值与 RMS 并回传结果。Windows 双向网关负责转发。

`网页提交 → Linux 中央排队与派发 → 双板计算 → 确认与结果回传 → 状态与审计`

- **调度与协议**：支持紧急优先、同级 FIFO 和每设备一个在途任务；实现会话去重、接受确认、心跳、超时与结果匹配。
- **双板实测**：接收 **93 个任务**，其中 **92 个板端计算成功、1 个主动断线测试保留为“结果未知”**；验证队列满拒绝和手动重试，最大绝对误差约 **4.69×10⁻⁶**。
- **工程验证**：普通及 ASan / UBSan 构建均通过 **176 项 Python 测试**，共享固件通过 **3 项 CTest**；另完成网页提交的六个真实任务验算。
- **运维 Agent**：接入真实 GLM，通过 `query_status` / `read_report` 完成两轮请求的工具调用闭环，展示证据与调用轨迹，支持调用预算、失败回退和离线规则解释。
- **网页工作台**：EdgeScope 提供实时任务派发与状态查看，并保留独立的历史实验分析、聊天和分组指标；模型工具保持只读，任务提交由用户操作。

<sub>已完成双板实物验收；计算样本为合成数据，93 任务记录包含预期故障测试。Agent 当前读取配置的历史状态与报告，实时派发由独立入口处理。</sub>

<sub>C / C++ · Linux / POSIX / poll · ESP32-C3 / Arduino · Wi-Fi / TCP / 串口 · Python · Tool Calling</sub>

**[查看仓库 →](https://github.com/BJTURylynn/esp32-linux-edge-scheduler)** · [中央派发设计](https://github.com/BJTURylynn/esp32-linux-edge-scheduler/blob/main/docs/central-dispatch.md) · [实物记录与网页截图](https://github.com/BJTURylynn/esp32-linux-edge-scheduler/blob/main/docs/evidence/central-dispatch/README.md) · [真实模型验证](https://github.com/BJTURylynn/esp32-linux-edge-scheduler/blob/main/docs/live-model.md)

<details>
<summary>查看第二版工作台实测截图</summary>

![EdgeScope 双板任务完成与结果查看](https://raw.githubusercontent.com/BJTURylynn/esp32-linux-edge-scheduler/main/docs/evidence/central-dispatch/screenshots/live-completed.jpg)

<sub>已归档实验截图；设备在线状态以本机当前运行服务为准。</sub>

</details>

---

### 02 / SupplyLens Agent

**采购到货异常分析助手：查订单、核对异常、检索 SOP，生成带证据的报告。**

使用 LangGraph 编排订单快照、异常计算和 SOP 检索三类工具，由 Python 规则计算业务事实，模型结合工具结果组织回答。支持自然语言查询、多轮跟进、Excel/CSV 导入及报告下载。

`业务快照 → 异常计算 → SOP 检索 → 引用校验 → 分析报告`

- **数据与交互**：支持六类业务表的字段映射、预览校验和事务写入，区分已确认异常与信息缺口。
- **工程验证**：通过 **186 项离线测试、30 个固定 Demo 案例**；完成真实 MySQL 接入及 SQLite → MySQL 逐行校验迁移。
- **模型联调**：GLM 对模拟订单完成单例工具调用，保留报告、业务证据及调用轨迹。

<sub>当前使用模拟业务资料验证；固定 Demo 验收与真实模型单例联调分别记录。</sub>

<sub>Python · LangGraph · FastAPI · Streamlit · SQLAlchemy · SQLite / MySQL · pytest</sub>

**[查看仓库 →](https://github.com/BJTURylynn/supplylens-agent)** · [演示与截图](https://github.com/BJTURylynn/supplylens-agent#演示) · [验证记录](https://github.com/BJTURylynn/supplylens-agent/blob/main/docs/validation.md)


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
| Agent 与应用 | LangGraph、FastAPI、Streamlit、GLM 工具调用、只读运维工作台、SOP 检索与引用校验 |
| 边缘系统与通信 | ESP32-C3 / Arduino / ESP-IDF、Linux / POSIX / poll、Wi-Fi / TCP / USB 串口、中央派发与板端计算 |
| 数据与验证 | SQLAlchemy、SQLite / MySQL、pytest / unittest、ASan / UBSan、CTest、实物验算与调度审计 |
| 仿真与分析 | HFSS、Origin、信号处理与通信建模 |

<a id="connect"></a>

## 交流与合作

欢迎交流 **AI Agent、大模型应用、嵌入式软件与车联网**方向的实习机会。

项目复现、问题反馈或合作想法，可以在对应仓库发起 Issue。

<div align="center">

**[浏览我的 GitHub 仓库 →](https://github.com/BJTURylynn?tab=repositories)**

<sub>用项目连接 AI 与边缘设备。</sub>

</div>
