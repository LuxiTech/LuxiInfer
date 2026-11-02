<p align="center">
  <img src="assets/luxiinfer-banner.png" width="100%" alt="LuxiInfer — High-Performance On-Device AI" />
</p>

<h1 align="center">LuxiInfer</h1>

<div align="center">

**面向 Dense 与 MoE 模型的高效端侧 AI 推理，以自研核心算子、超低比特量化和动态专家调度，突破移动端计算与存储瓶颈。**

<sub>首阶段聚焦 Android · 支持 Dense 与 MoE 模型 · 本地推理</sub>

![当前平台：Android](https://img.shields.io/badge/Current-Android-3DDC84.svg) ![模型架构：Dense 与 MoE](https://img.shields.io/badge/Models-Dense%20%7C%20MoE-2563EB.svg) ![本地推理](https://img.shields.io/badge/Inference-On--device-0D9488.svg)

[🎬 实机演示](#demo) · [🚀 快速开始](#quick-start) · [📰 最新动态](#news) · [⚡ 性能表现](#performance) · [🧩 技术方案](#technology)

**简体中文** | [English](README_EN.md)

</div>

<a id="features"></a>

**LuxiInfer** 是陆兮科技打造的高性能端侧 AI 推理方案与应用，面向不同架构和规模的大模型、芯片平台和终端场景，贯通模型适配、算子优化、低比特量化、存储管理与运行时调度，致力于让更多模型在不同终端设备上高效运行。

当前阶段，LuxiInfer 聚焦 Android 手机，已在高通移动平台完成首批适配与验证，通过 Android App 提供本地推理体验。目前适配自研 LuxiLLM 模型，以及 Qwen 系列的 Dense 与 MoE 模型，支持文本对话，部分模型支持图文理解。

- 📱 **一键下载，本地离线运行**：提供开箱即用的 App 体验。在 App 中选择并下载模型后即可开始文本对话，或使用支持图文的模型进行图片理解。模型下载完成后，全流程支持手机本地离线推理，有助于保护数据隐私。
- ⚡ **底层算子自研，高效释放 NPU 算力**：当前阶段面向高通 Hexagon NPU，结合**自研算子**，优化计算和数据搬运，解决混合注意力模型在通用框架下调度频繁、访存开销大的问题，显著提升计算效率。
- 💾 **计算与存储协同，降低资源开销**：根据模型特点，结合**低比特量化、动态缓存和异步加载**等技术，优化权重存储、内存占用与运行时调度，让大参数模型也能适应手机端资源。
- 🧠 **一套方案，覆盖多种模型架构**：同一套端侧推理方案覆盖 **Dense 与 MoE** 架构。让用户既能体验 2B 模型的极速响应，也能在手机上跑通 35B 大模型进行复杂的文本问答与图文理解。

未来，LuxiInfer 将持续扩展对不同模型架构、芯片平台与运行环境的适配，推进更通用的端侧算子、量化与运行时解决方案，让高性能本地 AI 能力覆盖更丰富的终端场景。

<a id="demo"></a>

## 🎬 实机演示

以下介绍以 Qwen3.5-2B 和 Qwen3.6-35B-A3B 为代表的 Dense 与 MoE 模型演示。

*测试设备：一加 15（16 GB 运行内存 + 256 GB 存储）。*

<table width="100%">
  <tr>
    <td width="50%" align="center" valign="top">
      <img src="assets/demo-dense-qwen3.5-2b-vision-npu.gif" width="90%" alt="Qwen3.5-2B Dense 实机演示" />
      <br /><b>Dense · Qwen3.5-2B：输入处理与连续生成</b>
      <p><b>Prefill: 1158.16 tokens/s, Decode: 47.62 tokens/s</b></p>
    </td>
    <td width="50%" align="center" valign="top">
      <img src="assets/demo-moe-qwen3.6-35b-a3b-file-npu.gif" width="90%" alt="Qwen3.6-35B-A3B MoE 实机演示" />
      <br /><b>MoE · Qwen3.6-35B-A3B：手机本地大模型推理</b>
      <p><b>Prefill: 461.98 tokens/s, Decode: 13.34 tokens/s</b></p>
    </td>
  </tr>
</table>
<a id="quick-start"></a>

## 🚀 快速开始

<a id="supported"></a>

### 1. 设备与模型

目前支持以下四款模型，下载前请预留相应的手机存储空间：

<table width="100%">
  <thead>
    <tr>
      <th width="21%"><div align="center">模型</div></th>
      <th width="18%"><div align="center">参数规模</div></th>
      <th width="24%"><div align="center">支持能力</div></th>
      <th width="15%"><div align="center">所需存储空间</div></th>
      <th width="22%"><div align="center">支持的设备</div></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center">LuxiLLM-1.7B</td>
      <td align="center">1.7B</td>
      <td align="center">手机本地文本推理</td>
      <td align="center">约 1.59 G</td>
      <td align="center" valign="middle" rowspan="4"><div align="center">搭载高通<br>Snapdragon 8 Elite<br>Gen 5 芯片的安卓设备</div></td>
    </tr>
    <tr>
      <td align="center">Qwen3.5-0.8B（Dense）</td>
      <td align="center">0.8B</td>
      <td align="center">手机本地文本与图文推理</td>
      <td align="center">约 767 MB</td>
    </tr>
    <tr>
      <td align="center">Qwen3.5-2B（Dense）</td>
      <td align="center">2B</td>
      <td align="center">手机本地文本与图文推理</td>
      <td align="center">约 1.8 G</td>
    </tr>
    <tr>
      <td align="center">Qwen3.6-35B-A3B（MoE）</td>
      <td align="center">35B 总参数 / 约 3B 激活参数</td>
      <td align="center">手机本地文本与图文推理</td>
      <td align="center">约 10.9 G</td>
    </tr>
  </tbody>
</table>


<a id="download"></a>

### 2. 下载与安装

下载 [**LuxiInfer Android App**](https://github.com/LuxiTech/LuxiInfer/releases/download/v1.0.0/LuxiInfer-20261102-v1.0.0.apk)，在 Android 手机上安装并打开。

### 3. 加载模型，开始对话

- **选择模型。** 进入 App 模型库，按任务需要选择模型。
- **一键下载并加载。** 下载配套模型包，完成后加载模型。
- **开始本地对话。** 输入文字体验文本问答和流式生成；支持图文的模型也可以输入图片。

模型下载需要网络；下载完成后，即可在离线状态下使用手机本地推理。

<a id="news"></a>

## 📰 最新动态

- 📱 **[2026-11-02]** **LuxiInfer-Android v1.0.0** 发布，支持模型一键下载与手机 NPU 本地推理。
- 🚀 **[2026-10-23]** 完成 **35B-A3B MoE** 手机端部署，**Qwen3.6-35B-A3B MoE 实测**纯文本 Prefill 达到 **470.661 tokens/s**，图文 Decode 达到 **14.262 tokens/s**。
- ⚡ **[2026-10-20]** 完成 **Dense** 模型加速。实测 **Qwen3.5-2B 在** 4K 上下文下，Prefill 达到 **1441.75 tokens/s**，Decode 达到 **50.95 tokens/s**。

<a id="performance"></a>

## ⚡ 性能表现

<a id="small-model-performance"></a>

### 🚀 Dense 模型实测：Qwen3.5-0.8B / 2B

在 **4K 上下文**下，LuxiInfer 在 **高通 Snapdragon 8 Elite Gen 5** 上实现：

- **Qwen3.5-0.8B：** Prefill **1843.58 tokens/s**，Decode **90.33 tokens/s**。
- **Qwen3.5-2B：** Prefill **1441.75 tokens/s**，Decode **50.95 tokens/s**。

下图汇总 **Qwen3.5-0.8B / 2B** 在 **高通 Snapdragon 8 Elite** 与 **高通 Snapdragon 8 Elite Gen 5** 平台、**4K 上下文**下的推理速度：左侧为 **Decode（连续生成）**，右侧为 **Prefill（输入处理）**，单位均为 token/s，**数值越高，速度越快**。蓝色为 LuxiInfer，灰色为高通官方参考（ai-hub-models）；每组标出实测速度与速度比。

![Qwen3.5-0.8B / 2B 在高通 Snapdragon 8 Elite 与高通 Snapdragon 8 Elite Gen 5 平台上的 4K 上下文 NPU 推理性能对比：Prefill 最高 2.17 倍，Decode 最高 2.35 倍](<assets/qwen35-performance-chart-zh.png>)

对比高通官方参考数据，LuxiInfer 的 Prefill 速度最高达到 **2.17 倍**（Qwen3.5-2B，Snapdragon 8 Elite），Decode 速度最高达到 **2.35 倍**（Qwen3.5-0.8B，Snapdragon 8 Elite Gen 5）。

*Snapdragon 8 Elite 数据为性能测试结果，当前 App 的设备支持范围请以[设备与模型](#supported)表为准。*

### 🌟 自研模型实测：LuxiLLM-1.7B

在 **高通 Snapdragon 8 Elite Gen 5** 上，LuxiLLM-1.7B 的 NPU 实测 **Prefill** 在 4K 输入时达到 **2617.54 tokens/s**；**Decode** 在 4K 输出时达到 **44.66 tokens/s**；**KV Cache** 在 4K 档位仅占用 **62.95 MiB**。

下表汇总 1K–4K 档位的实测结果：

| Prefill 输入长度 | Prefill（tokens/s） | Decode 输出长度 | Decode（tokens/s） | KV Cache（MiB） |
| :---: | :---: | :---: | :---: | :---: |
| 1K | 2308.57 | 1K | 49.21 | 38.95 |
| 2K | 2503.93 | 2K | 47.44 | 46.95 |
| 3K | 2564.37 | 3K | 47.92 | 54.95 |
| 4K | 2617.54 | 4K | 44.66 | 62.95 |

LuxiLLM-1.7B 在中文理解、数学应用、常识推理和科学问答四项基准测试中，分别取得 **58.83（CMMLU）、63.00（GSM8K）、63.59（HellaSwag）和 45.82（ARC-Challenge）** 的得分。了解更多，请访问[陆兮科技官网](https://www.luxitech.cn/)。

<a id="moe-performance"></a>

### 🧠 MoE 模型实测：Qwen3.6-35B-A3B

在**不使用前瞻专家调度与投机解码技术**的情况下，LuxiInfer 实现高性能的手机端 35B MoE 推理：

-  **Decode 最高 14.262 tokens/s。** 支持手机本地连续生成，满足文本问答与图文交互需求。
-  **Prefill 最高 470.661 tokens/s。** 输入处理吞吐突破 400 tokens/s，加快长输入任务的处理。

> 💾 **35B MoE，低内存部署：** Qwen3.6-35B-A3B 在一台配备 **16 GiB 运行内存**的 **高通 Snapdragon 8 Elite Gen 5** 手机上本地运行，且峰值运行内存低至 **约 5 GiB**。

#### 📊 1024 → 1024 token 实测

**测试平台：高通 Snapdragon 8 Elite Gen 5；总上下文：2048 token。** 以下展示同一配置下的纯文本与图文实测结果，输入与输出长度均为 1024 token。

| 输入类型 | 输入 → 输出 token | Prefill（tokens/s） | Decode（tokens/s） |
| :---: | :---: | :---: | :---: |
| 纯文本 | 1024 → 1024 | 470.661 | 14.179 |
| 图文 | 1024 → 1024 | 370.344 | 14.262 |

*图文任务的首次响应还包含图片处理与视觉编码时间。*


<a id="technology"></a>

## 🧩 技术方案

LuxiInfer 面向不同模型架构和终端平台，协同优化模型算子、量化、存储与运行时调度，为 Dense 与 MoE 模型提供高效的端侧推理能力。当前版本基于 ExecuTorch 和高通原生 AI 加速技术栈，完成首批 Android 设备适配。

### 1. 混合注意力：核心计算与执行优化

混合注意力模型通过不同的计算模块处理序列信息，对端侧算子效率、状态管理和硬件执行能力提出了较高要求。

LuxiInfer 面向混合注意力模型的计算特点，结合自研算子与模型执行优化，围绕计算融合、状态复用和硬件加速等方向，提升模型在手机端的推理效率：

- **算子实现与计算融合：** 将关键计算进行融合，结合向量化和并行执行，减少中间数据搬运，提高端侧计算效率。
- **状态与访存优化：** 复用中间结果与工作状态，降低重复计算和内存读写开销。
- **硬件加速与并行：** 结合目标平台的硬件能力优化执行；当前实现利用 Hexagon 向量化与并行执行能力，提高 Prefill 和 Decode 的执行效率。

### 2. MoE 架构：专家计算与资源调度优化

对于大参数 MoE 模型，专家权重的存储与调度带来了新的部署挑战：虽然每次只激活部分专家，但完整权重仍需存放在设备上，**常驻内存、专家读取与加载等待**成为影响手机端推理的重要因素。

以 Qwen3.6-35B-A3B 为例，LuxiInfer 协同优化专家计算、模型存储与资源管理，重点包括：

- **2-bit 专家量化：** 压缩专家权重，降低模型存储占用和权重传输开销。
- **按需加载与动态缓存：** 根据运行需求加载和复用专家权重，降低常驻内存占用。实测同一层相邻 token 选中专家的重合率达到 **82%**。
- **Prefill 权重复用：** 优化专家权重复用和批量计算，提升长输入处理效率。
- **Decode 读算交叠：** 协同专家权重读取与模型计算，减少加载等待，提升连续生成效率。
- **跨阶段资源共享：** 在 Prefill 与 Decode 阶段复用专家缓存和运行状态，减少重复加载与资源开销。

<a id="contact"></a>

## 🤝 交流与合作

欢迎通过项目 Issues 反馈机型适配、部署问题和性能记录。提交问题时请附手机 / SoC、系统版本、App / 模型版本、关键配置及运行日志。

面向手机、边缘设备与本地 AI 应用，陆兮科技提供模型适配、部署集成与性能优化的技术交流与合作。

- 技术交流与商务合作：[LuxiTech@luxitech.cn](mailto:LuxiTech@luxitech.cn)
- 陆兮科技：[GitHub · LuxiTech](https://github.com/LuxiTech)
- 相关项目：[LuxiChat-App](https://github.com/LuxiTech/LuxiChat-App)

感谢 ExecuTorch、Qualcomm AI 技术栈及 Qwen 开源模型社区。模型与第三方组件的来源、版本及许可说明见对应发布物。
