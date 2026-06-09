---
title: "The Best of Both Worlds: Bridging Quality and Diversity in Data Selection with Bipartite Graph"
title_zh: 两全其美：用二分图在数据选择中兼顾质量与多样性
authors: "Minghao Wu, Thuy-Trang Vu, Lizhen Qu, Gholamreza Haffari"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=nCoaJYNCcg"
tags: ["query:graph-llm"]
score: 7.0
evidence: 使用二分图模型进行数据选择以改进大语言模型微调
tldr: 针对大语言模型监督微调（SFT）中数据选择偏重质量或多样性导致次优训练的问题，本文提出GraphFilter方法：将数据集建模为句子与n-gram的二分图，设计乘性优先级函数平衡质量与多样性指标，迭代选取高优先级句子并移除已覆盖的n-gram。实验证明该方法在多个基准上实现更优的模型性能，证实图建模有助于LLM数据选择。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-ncoajynccg/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1530, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ncoajynccg/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1642, \"height\": 539, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ncoajynccg/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 774, \"height\": 424, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ncoajynccg/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 858, \"height\": 622, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-ncoajynccg/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1644, \"height\": 1481, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ncoajynccg/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 545, \"height\": 449, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ncoajynccg/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 804, \"height\": 301, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ncoajynccg/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 843, \"height\": 459, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ncoajynccg/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 856, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ncoajynccg/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 839, \"height\": 263, \"label\": \"Table\"}]"
motivation: 大语言模型监督微调的数据选择常难以同时保证质量与多样性，影响训练效果。
method: 提出GraphFilter，将数据集建模为句子与n-gram的二分图，并利用乘性优先级函数迭代选取句子。
result: 该方法在多个基准上蒸馏出性能更优的学生模型，验证了图增强数据选择的有效性。
conclusion: 图建模为LLM数据选择提供了新的视角，可有效平衡质量与多样性，提升微调效率。
---

## Abstract
The performance of large language models (LLMs) is strongly influenced by the quality and diversity of data used during supervised fine-tuning (SFT). However, current data selection methods often prioritize one aspect over the other, resulting in suboptimal training outcomes. To address this, we formulate data selection as a set cover problem and present GraphFilter, a novel approach that balances both quality and diversity in data selection. GraphFilter models the dataset as a bipartite graph connecting sentences to their constituent n-grams, then employs a priority function that combines quality and diversity metrics multiplicatively. GraphFilter iteratively selects sentences with the highest priority, removes covered n-grams from the bipartite graph, and recomputes priorities to reflect the changing data landscape. We validate GraphFilter using three model backbones across six widely-used benchmarks, demonstrating that it outperforms nine existing baselines in both model performance and computational efficiency. Further analysis shows that our design choices lead to more effective subset selection, underscores the value of instruction diversity, and provides insights into how quality and diversity interact with different subset sizes.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义
大型语言模型（LLMs）在监督微调（SFT）阶段，数据的**质量**与**多样性**共同决定最终性能。然而现有数据选择方法常偏重其一：
- 过分追求质量可能忽视语言模式的广度，导致过拟合；
- 一味强调多样性则可能引入低质数据，损害模型表现。
因此，如何在给定预算下选出**同时兼顾质量与多样性**的子集成为了开放挑战。作者将其形式化为**集合覆盖问题**，旨在用较小句子集合覆盖尽可能多的 n‑gram，同时确保句子本身高质量。

---

### 2. 论文提出的方法论
**核心思想**：将数据选择建模为二分图上的集合覆盖问题，利用乘性优先级函数在迭代中平衡质量与多样性。

**关键技术细节**：
- **二分图建模**：  
  节点集 $U$ (句子) 与 $V$ (n‑gram)，边表示句子包含某 n‑gram。采用 unigram、bigram、trigram 的组合。
- **优先级函数**（平衡机制）：  
  \[
  \phi(u) = \text{QUALITY}(u) \times \text{DIVERSITY}(u)
  \]
  - 质量度量：`SUPERFILTER`，即 $ \text{PPL}(y|x)/\text{PPL}(y) $，衡量回答对指令的信息量；
  - 多样性度量：句子中所有 n‑gram 的 TF‑IDF 分数之和，反映覆盖价值。
- **迭代选择算法**（GraphFilter）：  
  1. 初始化空集 $S$；
  2. 每次选取优先级最高的句子 $u^*$；
  3. 将 $u^*$ 及其覆盖的 n‑gram 从图中删除，更新剩余句子的多样性得分（因 TF‑IDF 基于当前图）；
  4. 重复直至选满 $k$ 条句子。
- **实现优化**：使用最大堆加速优先级选取，复杂度从 $O(N)$ 降至 $O(\log N)$；若不需质量重排序，可在 CPU 上快速运行。

**理论联系**：当所有句子具有相同优先级时，该贪心算法对应集合覆盖问题的 $H(r)$‑近似，其中 $r$ 为句子最大 n‑gram 度。

---

### 3. 实验设计
**数据集与预算**：
- 源数据集：**Magpie**（由 LLaMA‑3‑70B‑Instruct 生成，300K 条指令‑响应对）。
- 选择子集：从全集中用不同方法选取 **10K** 条（另有 1K、5K、50K 等预算对比）。

**模型骨干**：
- Gemma‑2‑2B、Mistral‑7B‑v0.3、LLaMA‑3‑8B。

**评测基准**：
- 标准化基准（准确率）：MMLU、ARC、HellaSwag、GSM8K，取宏平均 $\mu_{\text{BENCH}}$。
- LLM‑as‑Judge 基准：AlpacaEval‑2.0（长度控制胜率 LC 和原始胜率 WR）与 MT‑Bench（$\mu_{\text{MT}}$），并以 GPT‑4o 作为评判，汇总为 $\mu_{\text{LLM}}$。
- 最终综合指标 $\mu_{\text{ALL}}$ 为上述六项成绩的宏平均。

**对比方法**（共 9 个基线）：
- 启发式：Random、Longest。
- 质量导向：Perplexity、ArmoRM、Alpagasus（用 Gemma‑2‑27B‑IT 替代 GPT‑3.5）、Deita、SuperFilter。
- 多样性导向：KMeans（BGE‑Large‑en‑v1.5 嵌入，10K 簇）和 InsTag。

所有微调均采用统一超参数（batch size 64，learning rate 2e‑5，warmup 0.05，训练 3 epochs）。

---

### 4. 资源与算力
- **训练算力**：所有模型使用 **2 × A100 80GB GPU（PCIe 连接）** 进行微调。
- **选择效率**：在 A100 80G GPU + 20 CPU 核心的机器上对比各方法选择 10K 样本的耗时：
  - GraphFilter（含 SuperFilter 质量度量）耗时 **2.48 小时**；
  - GraphFilter 不使用优先级 $\phi(u)$（纯 CPU）仅需 **0.53 小时**；
  - 相比之下，Alpagasus 耗时 32.34 小时，InsTag 25.48 小时，ArmoRM 5.93 小时。

论文并未详细列出每次实验的具体 GPU 小时数，但已给出上述参考值。

---

### 5. 实验数量与充分性
- **主实验**：3 种模型 × 10 种方法（含基线）在 6 个基准上的全面对比，产生 3 张完整表格。
- **消融与分析实验**：
  - n‑gram 组合（Unigram/Bigram/Trigram）；
  - 优先级函数中的质量和多样性组件分别去除或替换；
  - 质量度量的可替换性（用 Perplexity、ArmoRM、Deita 等）；
  - n‑gram 阶数从 1 到 5 的性能‑效率曲线；
  - 对指令、响应、或二者同时应用 GraphFilter 的影响；
  - 不同数据选择预算（1K ~ 200K）下质量与多样性的作用变化；
  - 子集的质量‑多样性散点图与 t‑SNE 语义多样性可视化。
- **实验公平性**：所有方法采用相同数据源、预算、微调设置，基线均利用官方实现或合理替代，对比客观。
- **覆盖性**：从模型规模、基准类型到预算规模，实验设计相当全面，足以支撑结论。

---

### 6. 论文的主要结论与发现
- GraphFilter 在所有模型和基准上均显著优于 9 种基线，$\mu_{\text{ALL}}$ 提升幅度最高达 **+3.38**（LLaMA‑3‑8B 相较 Longest）。
- 单纯的质量方法存在基准偏差（如 ArmorRM 擅长 AlpacaEval 但其他任务弱），而 GraphFilter 通过融合多样性回避了此缺陷。
- 计算效率极高：无需 GPU 即可在 0.53 小时内完成选取，比 Alpagasus 快 **61 倍**。
- 指令的多样性对最终性能至关重要，单纯对响应或同时对二者应用 GraphFilter 反不如仅对指令。
- 数据预算较小时，质量优先更重要；预算增大后，多样性的价值上升，GraphFilter 在不同尺度下均稳健。
- Trigrams (n=3) 是性能与效率的最佳平衡点。

---

### 7. 优点
- **问题形式化新颖**：将数据选择与集合覆盖理论结合，提供了可解释的贪心框架。
- **图结构灵活**：二分图自然支持 n‑gram 覆盖计数，迭代更新机制可动态反映多样性变化。
- **质量与多样性乘性融合**：简单且有效，且质量度量可即插即用，适应不同场景。
- **实验扎实**：覆盖多种模型家族与评测范式，从标准知识、推理到开放指令跟随；同时包含丰富的消融和多维度分析。
- **实用性强**：CPU 友好，选择过程极快，易于落地。

---

### 8. 不足与局限
- **语言与领域局限**：实验仅基于英文 Magpie 数据集，未验证跨语言或跨领域（如代码、医疗）的泛化性。
- **仅关注指令覆盖**：方法仅应用于指令部分，完全忽略了响应的多样性或质量，尽管论文指出指令多样性更关键，但在某些场景下响应的质量同样重要。
- **n‑gram 表示有限**：基于表层 n‑gram 可能无法捕捉深层语义或任务相关多样性；在需复杂推理的数据上，n‑gram 覆盖与价值可能存在偏差。
- **质量度量依赖外部模型**：默认使用 SuperFilter 依赖 GPT‑2 计算困惑度，可能受小模型能力限制；文中展示了可替换性，但未系统评估不同质量度量对最终排名稳定性的影响。
- **缺乏多轮/对话数据验证**：实验数据为单轮指令‑回答，未涉及多轮对话或偏好对齐数据。
- **超参敏感性未深入**：如 TF‑IDF 加权、n‑gram 阶数选择可能需根据数据特点调整，论文未给出自动化选择的指导。

（完）
