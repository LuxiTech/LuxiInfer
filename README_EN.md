<p align="center">
  <img src="assets/luxiinfer-banner.png" width="100%" alt="LuxiInfer — High-Performance On-Device AI" />
</p>

<h1 align="center">LuxiInfer</h1>

<div align="center">

**Efficient on-device inference for Dense and MoE models, overcoming mobile compute and storage bottlenecks with custom core operators, ultra-low-bit quantization, and dynamic expert scheduling.**

<sub>Initial focus: Android · Dense and MoE models · On-device inference</sub>

![Current platform: Android](https://img.shields.io/badge/Current-Android-3DDC84.svg) ![Models: Dense and MoE](https://img.shields.io/badge/Models-Dense%20%7C%20MoE-2563EB.svg) ![On-device inference](https://img.shields.io/badge/Inference-On--device-0D9488.svg)

[🎬 Live Demos](#demo) · [🚀 Quick Start](#quick-start) · [📰 News](#news) · [⚡ Performance](#performance) · [🧩 Technology](#technology)

[简体中文](README.md) | **English**

</div>

<a id="features"></a>

**LuxiInfer** is LuxiTech’s high-performance on-device AI inference solution and application. Designed for large models of different architectures and scales, chip platforms, and device scenarios, it brings together model adaptation, operator optimization, low-bit quantization, storage management, and runtime scheduling, with the goal of running more models efficiently across a wider range of devices.

The current phase focuses on Android phones, with initial adaptation and validation completed on Qualcomm mobile platforms. The Android app provides local inference and currently supports LuxiTech’s own LuxiLLM models, as well as Dense and MoE models from the Qwen series. These support text conversations, and selected models also support image understanding.

- 📱 **One-tap download and offline inference:** Enjoy an out-of-the-box app experience. Select and download a model in the app to start text conversations, or use a model that supports image understanding. Once the model is downloaded, inference runs entirely on the phone without an internet connection, helping keep your data private.
- ⚡ **Custom low-level operators make the most of the NPU:** In the current phase, LuxiInfer targets the Qualcomm Hexagon NPU and uses **custom operators** to optimize computation and data movement. This addresses frequent scheduling and memory-access overhead in hybrid-attention models running on general-purpose frameworks, improving computational efficiency.
- 💾 **Coordinated compute and storage reduce resource use:** **Low-bit quantization, dynamic caching, and asynchronous loading** are tailored to each model to optimize weight storage, memory usage, and runtime scheduling, making large models practical on phones.
- 🧠 **One solution for multiple model architectures:** The same on-device inference solution supports both **Dense and MoE** architectures. Users can enjoy fast responses from a 2B model or run a 35B model on a phone for complex text and image-based tasks.

Looking ahead, LuxiInfer will continue to expand support for model architectures, chip platforms, and runtime environments, developing more general on-device operators, quantization, and runtime solutions to bring high-performance local AI to a wider range of devices and use cases.

<a id="demo"></a>

## 🎬 Live Demos

The demos below feature Qwen3.5-2B and Qwen3.6-35B-A3B as examples of Dense and MoE models.

*Test device: OnePlus 15 (16 GB RAM + 256 GB storage).*

<table width="100%">
  <tr>
    <td width="50%" align="center" valign="top">
      <img src="assets/demo-dense-qwen3.5-2b-vision-npu.gif" width="90%" alt="Qwen3.5-2B Dense model input processing and continuous generation demo" />
      <br /><b>Dense · Qwen3.5-2B: Fast processing and generation</b>
      <p><b>Prefill: 1158.16 tokens/s, Decode: 47.62 tokens/s</b></p>
    </td>
    <td width="50%" align="center" valign="top">
      <img src="assets/demo-moe-qwen3.6-35b-a3b-file-npu.gif" width="90%" alt="Qwen3.6-35B-A3B MoE model demo" />
      <br /><b>MoE · Qwen3.6-35B-A3B: On-device large-model inference</b>
      <p><b>Prefill: 461.98 tokens/s, Decode: 13.34 tokens/s</b></p>
    </td>
  </tr>
</table>

<a id="quick-start"></a>

## 🚀 Quick Start

<a id="supported"></a>

### 1. Devices and Models

The following four models are currently supported. Make sure your phone has enough storage space before downloading:

<table width="100%">
  <thead>
    <tr>
      <th width="21%"><div align="center">Model</div></th>
      <th width="18%"><div align="center">Parameters</div></th>
      <th width="24%"><div align="center">Capabilities</div></th>
      <th width="15%"><div align="center">Storage required</div></th>
      <th width="22%"><div align="center">Supported devices</div></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center">LuxiLLM-1.7B</td>
      <td align="center">1.7B</td>
      <td align="center">On-device text inference</td>
      <td align="center">Approx. 1.59 G</td>
      <td align="center" valign="middle" rowspan="4"><div align="center">Android devices powered by<br>Qualcomm Snapdragon<br>8 Elite Gen 5</div></td>
    </tr>
    <tr>
      <td align="center">Qwen3.5-0.8B (Dense)</td>
      <td align="center">0.8B</td>
      <td align="center">On-device text and image inference</td>
      <td align="center">Approx. 767 MB</td>
    </tr>
    <tr>
      <td align="center">Qwen3.5-2B (Dense)</td>
      <td align="center">2B</td>
      <td align="center">On-device text and image inference</td>
      <td align="center">Approx. 1.8 G</td>
    </tr>
    <tr>
      <td align="center">Qwen3.6-35B-A3B (MoE)</td>
      <td align="center">35B total / approx. 3B active</td>
      <td align="center">On-device text and image inference</td>
      <td align="center">Approx. 10.9 G</td>
    </tr>
  </tbody>
</table>

<a id="download"></a>

### 2. Download and Install

Download the [**LuxiInfer Android App**](https://github.com/LuxiTech/LuxiInfer/releases/download/v1.0.0/LuxiInfer-20261102-v1.0.0.apk), then install and open it on your Android phone.

### 3. Load a Model and Start Chatting

- **Choose a model.** Open the app's model library and select a model for your task.
- **Download and load it.** Download the corresponding model package, then load the model.
- **Start an on-device conversation.** Enter text to try question answering and streaming generation, or provide an image when using a model that supports image understanding.

An internet connection is required to download a model. Once downloaded, the model can run locally on your phone offline.

<a id="news"></a>

## 📰 News

- 📱 **[2026-11-02]** **LuxiInfer-Android v1.0.0** released, with one-tap model downloads and on-device NPU inference.
- 🚀 **[2026-10-23]** Deployed a **35B-A3B MoE** model on a phone. In tests, **Qwen3.6-35B-A3B MoE** reached **470.661 tokens/s** for text-only prefill and **14.262 tokens/s** for multimodal decode.
- ⚡ **[2026-10-20]** Completed **Dense** model acceleration. In tests with a 4K context, **Qwen3.5-2B** reached **1441.75 tokens/s** for prefill and **50.95 tokens/s** for decode.

<a id="performance"></a>

## ⚡ Performance

<a id="small-model-performance"></a>

### 🚀 Dense Model Benchmarks: Qwen3.5-0.8B / 2B

With a **4K context**, LuxiInfer achieves the following on **Qualcomm Snapdragon 8 Elite Gen 5**:

- **Qwen3.5-0.8B:** Prefill **1843.58 tokens/s**, decode **90.33 tokens/s**.
- **Qwen3.5-2B:** Prefill **1441.75 tokens/s**, decode **50.95 tokens/s**.

The chart below compares inference speeds for **Qwen3.5-0.8B / 2B** with a **4K context** on **Qualcomm Snapdragon 8 Elite** and **Qualcomm Snapdragon 8 Elite Gen 5**. The left section shows **decode (token generation)** and the right section shows **prefill (input processing)**, both in tokens/s; **higher is faster**. Blue represents LuxiInfer and gray represents Qualcomm's official reference (ai-hub-models). Each group shows the measured speeds and their ratio.

![4K-context NPU inference performance comparison for Qwen3.5-0.8B / 2B on Qualcomm Snapdragon 8 Elite and Snapdragon 8 Elite Gen 5: up to 2.17× prefill and 2.35× decode](<assets/qwen35-performance-chart-zh.png>)

Compared with Qualcomm's reference results, LuxiInfer achieves up to **2.17× the prefill speed** (Qwen3.5-2B on Snapdragon 8 Elite) and **2.35× the decode speed** (Qwen3.5-0.8B on Snapdragon 8 Elite Gen 5).

*Snapdragon 8 Elite results are benchmark data; see [Devices and Models](#supported) for current app support.*

### 🌟 In-House Model Benchmarks: LuxiLLM-1.7B

On **Qualcomm Snapdragon 8 Elite Gen 5**, LuxiLLM-1.7B achieved the following NPU results: **Prefill:** **2617.54 tokens/s** with a 4K-token input; **Decode:** **44.66 tokens/s** with a 4K-token output; and **KV Cache:** **62.95 MiB** in the 4K test.

The table below summarizes the measured results across the 1K–4K test settings:

| Prefill input length | Prefill (tokens/s) | Decode output length | Decode (tokens/s) | KV Cache (MiB) |
| :---: | :---: | :---: | :---: | :---: |
| 1K | 2308.57 | 1K | 49.21 | 38.95 |
| 2K | 2503.93 | 2K | 47.44 | 46.95 |
| 3K | 2564.37 | 3K | 47.92 | 54.95 |
| 4K | 2617.54 | 4K | 44.66 | 62.95 |

LuxiLLM-1.7B scored **58.83 on CMMLU**, **63.00 on GSM8K**, **63.59 on HellaSwag**, and **45.82 on ARC-Challenge**, covering Chinese language understanding, math word problems, commonsense reasoning, and science question answering, respectively. Learn more on the [LuxiTech website](https://www.luxitech.cn/).

<a id="moe-performance"></a>

### 🧠 MoE Model Benchmarks: Qwen3.6-35B-A3B

LuxiInfer delivers high-performance on-device inference for a 35B MoE model **without lookahead expert scheduling or speculative decoding**:

- **Decode up to 14.262 tokens/s.** Supports continuous on-device generation for text questions and image-based interactions.
- **Prefill up to 470.661 tokens/s.** Input processing throughput exceeds 400 tokens/s, speeding up long-input tasks.

> 💾 **35B MoE with low memory usage:** Qwen3.6-35B-A3B runs locally on a **Qualcomm Snapdragon 8 Elite Gen 5** phone with **16 GiB of RAM**, with peak runtime memory usage as low as **approximately 5 GiB**.

#### 📊 1024 → 1024 Token Benchmarks

**Test platform: Qualcomm Snapdragon 8 Elite Gen 5; total context: 2048 tokens.** The following results show text-only and multimodal tests under the same configuration, with 1024 input tokens and 1024 output tokens.

| Input type | Input → output tokens | Prefill (tokens/s) | Decode (tokens/s) |
| :---: | :---: | :---: | :---: |
| Text only | 1024 → 1024 | 470.661 | 14.179 |
| Text and image | 1024 → 1024 | 370.344 | 14.262 |

*Time to first response for multimodal tasks also includes image processing and visual encoding.*

<a id="technology"></a>

## 🧩 Technology

LuxiInfer coordinates optimization of model operators, quantization, storage, and runtime scheduling across different model architectures and device platforms, providing efficient on-device inference for Dense and MoE models. The current version builds on ExecuTorch and Qualcomm’s native AI acceleration stack, with initial Android device support.

### 1. Hybrid Attention: Core Computation and Execution Optimization

Hybrid-attention models use different computational modules to process sequence information, placing demands on on-device operator efficiency, state management, and hardware execution.

LuxiInfer combines custom operators with model execution optimizations tailored to hybrid-attention models, improving mobile inference efficiency through fused computation, state reuse, and hardware acceleration:

- **Operator implementation and fused computation:** Fuse key computations and use vectorization and parallel execution to reduce intermediate data transfers and improve on-device efficiency.
- **State and memory-access optimization:** Reuse intermediate results and working state to reduce redundant computation and memory access.
- **Hardware acceleration and parallel execution:** Optimize execution for the target platform. The current implementation uses Hexagon vectorization and parallel execution to improve Prefill and Decode efficiency.

### 2. MoE Architecture: Expert Computation and Resource Scheduling Optimization

For large-parameter MoE models, expert weight storage and scheduling present deployment challenges. Although only some experts are activated at a time, the full set of weights must still be stored on the device, making **resident memory, expert reads, and loading delays** important factors in mobile inference.

Using Qwen3.6-35B-A3B as an example, LuxiInfer coordinates expert computation, model storage, and resource management through the following optimizations:

- **2-bit expert quantization:** Compress expert weights to reduce model storage and weight transfer overhead.
- **On-demand loading and dynamic caching:** Load and reuse expert weights as needed to reduce resident memory use. Tests showed an **82% overlap** between experts selected for consecutive tokens in the same layer.
- **Prefill weight reuse:** Optimize expert weight reuse and batched computation to improve long-input processing efficiency.
- **Decode read-compute overlap:** Coordinate weight reads with model computation to reduce loading delays and improve decode efficiency.
- **Resource sharing across stages:** Reuse expert caches and runtime state across Prefill and Decode to reduce repeated loading and resource overhead.

<a id="contact"></a>

## 🤝 Contact and Collaboration

Please use project Issues to report device compatibility, deployment problems, and performance results. When submitting an issue, include your phone / SoC, OS version, app / model version, key settings, and runtime logs.

LuxiTech welcomes technical discussions and collaboration on model adaptation, deployment integration, and performance optimization for phones, edge devices, and local AI applications.

- Technical and business inquiries: [LuxiTech@luxitech.cn](mailto:LuxiTech@luxitech.cn)
- LuxiTech: [GitHub · LuxiTech](https://github.com/LuxiTech)
- Related project: [LuxiChat-App](https://github.com/LuxiTech/LuxiChat-App)

Thanks to the ExecuTorch, Qualcomm AI stack, and Qwen open-source model communities. See the corresponding releases for the sources, versions, and licensing information of models and third-party components.
