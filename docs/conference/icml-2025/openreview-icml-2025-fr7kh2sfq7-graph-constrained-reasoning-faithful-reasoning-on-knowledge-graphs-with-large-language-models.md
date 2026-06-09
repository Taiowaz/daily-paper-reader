---
title: "Graph-constrained Reasoning: Faithful Reasoning on Knowledge Graphs with Large Language Models"
title_zh: 图约束推理：基于知识图谱的大型语言模型忠实推理
authors: "Linhao Luo, Zicheng Zhao, Gholamreza Haffari, Yuan-Fang Li, Chen Gong, Shirui Pan"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Fr7kH2SFq7"
tags: ["query:graph-llm"]
score: 9.0
evidence: 将知识图谱结构融入LLM推理以实现忠实推理
tldr: 大型语言模型在推理中存在知识缺口与幻觉问题，现有知识图谱增强方法检索不准且遍历效率低。本文提出图约束推理框架GCR，将知识图谱结构信息融入LLM推理过程，约束生成路径，确保推理忠实于图谱事实。实验表明GCR有效消除幻觉，提升知识图谱上的推理准确性，为结构化与非结构化推理的融合提供了新思路。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-fr7kh2sfq7/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 355, \"height\": 427, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fr7kh2sfq7/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1498, \"height\": 1194, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fr7kh2sfq7/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 852, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fr7kh2sfq7/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 573, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fr7kh2sfq7/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 698, \"height\": 358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fr7kh2sfq7/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1426, \"height\": 982, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fr7kh2sfq7/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 684, \"height\": 609, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fr7kh2sfq7/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1617, \"height\": 365, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fr7kh2sfq7/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1752, \"height\": 174, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fr7kh2sfq7/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1716, \"height\": 727, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1086, \"height\": 964, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1083, \"height\": 352, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 868, \"height\": 194, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 787, \"height\": 573, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1464, \"height\": 391, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1461, \"height\": 317, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 711, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1082, \"height\": 328, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 683, \"height\": 229, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1779, \"height\": 269, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 748, \"height\": 272, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1320, \"height\": 248, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 477, \"height\": 141, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 775, \"height\": 231, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 737, \"height\": 315, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1778, \"height\": 207, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 998, \"height\": 249, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1609, \"height\": 357, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fr7kh2sfq7/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1610, \"height\": 309, \"label\": \"Table\"}]"
motivation: LLM推理存在幻觉和知识缺口，现有KG增强方法难以准确检索和高效遍历。
method: 提出图约束推理框架GCR，将知识图谱结构信息融入LLM推理以约束生成。
result: GCR实现了忠实推理，消除了幻觉，在知识图谱问答等任务上表现优异。
conclusion: GCR为结构化知识与非结构化推理的融合提供了可扩展的方案。
---

## Abstract
Large language models (LLMs) have demonstrated impressive reasoning abilities, but they still struggle with faithful reasoning due to knowledge gaps and hallucinations. To address these issues, knowledge graphs (KGs) have been utilized to enhance LLM reasoning through their structured knowledge. However, existing KG-enhanced methods, either retrieval-based or agent-based, encounter difficulties in accurately retrieving knowledge and efficiently traversing KGs at scale. In this work, we introduce graph-constrained reasoning (GCR), a novel framework that bridges structured knowledge in KGs with unstructured reasoning in LLMs. To eliminate hallucinations, GCR ensures faithful KG-grounded reasoning by integrating KG structure into the LLM decoding process through KG-Trie, a trie-based index that encodes KG reasoning paths. KG-Trie constrains the decoding process, allowing LLMs to directly reason on graphs and generate faithful reasoning paths grounded in KGs. Additionally, GCR leverages a lightweight KG-specialized LLM for graph-constrained reasoning alongside a powerful general LLM for inductive reasoning over multiple reasoning paths, resulting in accurate reasoning with zero reasoning hallucination. Extensive experiments on several KGQA benchmarks demonstrate that GCR achieves state-of-the-art performance and exhibits strong zero-shot generalizability to unseen KGs without additional training.

---

## 论文详细总结（自动生成）

# 论文总结：图约束推理——基于知识图谱的大型语言模型忠实推理

## 1. 论文的核心问题与整体含义

- **背景**：大型语言模型（LLMs）在推理任务中展现强大能力，但因**知识缺口**和**幻觉**问题，生成的推理过程常不可靠、包含事实错误。
- **问题**：现有将知识图谱（KG）用于增强LLM推理的方法，无论是**检索式**（依赖外部检索器，难以准确捕捉图结构）还是**代理式**（多轮交互，计算成本高、延迟大），仍存在严重幻觉，且难以在规模上高效遍历KG。
- **目标**：提出**图约束推理（Graph-constrained Reasoning, GCR）** 框架，将KG的结构化知识直接融入LLM解码过程，**消除推理幻觉**，实现忠实于图谱事实的推理，并支持多路径归纳，提升推理准确性。

## 2. 论文提出的方法论

GCR由三个核心组件构成，形成从KG到LLM推理的闭环。

### 2.1 知识图谱前缀树（KG-Trie）构建

- 将KG中从问题实体出发、限定跳数`L`的推理路径用**宽度优先搜索（BFS）** 提取。
- 路径按模板格式化为字符串，经LLM分词器切分为token序列。
- 将所有这些token序列构建为**前缀树（Trie）** 索引，支持常数时间内检查生成的前缀是否有效。

$$
\mathbf{W}_z = \text{BFS}(\mathcal{G}, \mathcal{E}_q, L), \quad
\mathbf{T}_z = \text{Tokenizer}(\mathbf{W}_z), \quad
\mathcal{C}_\mathcal{G} = \text{Trie}(\mathbf{T}_z)
$$

### 2.2 图约束解码（Graph-constrained Decoding）

- 使用**轻量级KG专用LLM**（参数`\phi`）在`KG-Trie`约束下自回归生成推理路径`w_z`及假设答案`a`。
- 约束函数`\mathcal{C}_\mathcal{G}`检查每一步生成token的前缀是否在Trie中，若有效则继续，否则强制选择合法路径。推理路径生成完成后切换回常规解码生成答案。
- 模型通过**微调**优化：训练数据使用问题-答案对及KG中最短推理路径，最大化条件概率`P_\phi(a, w_z|q)`。
- 推理时采用**束搜索**一次生成`K`条路径和对应答案。

关键公式：

$$
P_\phi(a, w_z|q) = P_\phi(a|q, w_z) \prod_{i=1}^{|w_z|} P_\phi(w_z^i|q, w_z^{1:i-1}) \; \mathcal{C}_\mathcal{G}(w_z^i|w_z^{1:i-1})
$$

### 2.3 图归纳推理（Graph Inductive Reasoning）

- 将束搜索得到的`K`条路径及假设答案`\mathcal{Z}_K`输入**通用LLM**（如ChatGPT、GPT-4o-mini），利用其强归纳能力，从多条路径中整合信息，生成最终答案。
- 通用LLM直接以提示词方式整合多路径，无需额外微调。

## 3. 实验设计

### 3.1 数据集与基准

- **主测试**：WebQSP、CWQ（基于Freebase KG），评测**Hit**和**F1**。
- **零样本迁移**：FreebaseQA（Freebase KG）、CSQA（ConceptNet）、MedQA（医学KG），评测**准确率**。
- 构造微调数据：从训练集问题-答案对中提取KG中最短路径作为标注。

### 3.2 对比方法（22个基线）

- **LLM推理方法**：Qwen2（0.5B~7B）、Llama-2-7B、Llama-3.1-8B、ChatGPT、GPT-4o-mini，以及CoT、Self-Consistency等策略。
- **图推理方法**：GraftNet、NSM、SR+NSM、ReaRev、UniKGQA。
- **KG+LLM方法**：检索式（KD-CoT、EWEK-QA、RoG、GNN-RAG及其变体）和代理式（ToG、EffiQA）。

### 3.3 评估维度

- 主结果表、效率对比（平均运行时间、LLM调用次数、输入token数）。
- 消融实验（移除KG专用LLM或通用LLM）。
- 不同容量/类型的LLM对性能影响。
- 参数分析：束宽`K`、KG-Trie路径跳数`L`。
- 幻觉分析：对比有无约束时的答案命中率及**忠实推理比例**（路径是否能在KG中找到）。
- 零样本泛化实验。

## 4. 资源与算力

- **训练硬件**：**2块NVIDIA A100-80G GPU**。
- **训练配置**：批量大小4，学习率2e-5，余弦学习率调度，warmup比例0.03，**训练3个epoch**。
- 不同模型训练时间示例：Qwen2-0.5B约3.47小时，Llama-3.1-8B约14.52小时，显存占用80~85 GB。
- 推理实验在**单卡A100-80G**上进行。

## 5. 实验数量与充分性

- 实验覆盖**2个主数据集 + 3个零样本数据集**，对比**22个基线**，包含**消融、参数分析、幻觉诊断、效率对比、案例研究**等，实验设计全面。
- 各对比方法均按要求复现或直接引用原文结果，**公平性**较好（如统一使用相同KG子图、相同问题链接等）。
- 统计分析包括：Hit/F1/准确率、运行时间、LLM调用数、token消耗、忠实推理比例等，**维度较丰富**，但未报告多次运行的方差/置信区间。

## 6. 论文的主要结论与发现

- **性能领先**：GCR在WebQSP和CWQ上Hit分别达到92.6%和72.7%，超越所有基线，F1也最优。
- **零幻觉推理**：引入KG-Trie约束后，正确回答中的推理路径**100%可被KG验证**，无约束时幻觉严重（仅48.1%~62.4%忠实）。
- **高效**：在相近或更短运行时间内，GCR仅需约3.6秒、2次LLM调用和约2231个token，低于代理式方法（ToG约16秒、11.6次调用、7000+token）。
- **轻量专用LLM + 通用LLM协同有效**：0.5B专用模型配合ChatGPT即可超越多数大型模型，微调后能力显著提升。
- **零样本泛化强**：在从未训练的FreebaseQA、CSQA上，相对于ChatGPT/GPT-4o-mini分别提升了约7~8个百分点；在医学KG上提升较小，可能由于领域知识特殊性。

## 7. 优点

- **创新架构**：将KG结构编码为Trie直接约束解码，首次实现LLM在图上“解码即推理”，保证生成路径的忠实性。
- **高效率**：利用Trie索引在常数时间检查合法性，结合束搜索并行生成多条路径，避免多轮代理交互的高延迟。
- **模块化与协同**：专用LLM负责图内探索，通用LLM负责归纳整合，分工明确，可灵活替换不同模型。
- **强零样本能力**：KG约束与专用LLM解耦，切换到新KG时只需重建Trie，无需重训模型，跨KG迁移方便。
- **实验扎实**：覆盖面广、对比基线多、幻觉评价直接，且有零样本和效率分析，可复现性强（提供代码和数据）。

## 8. 不足与局限

- **KG依赖性与不完整性**：零幻觉定义仅以KG为基准，若KG本身缺失或错误，生成的路径可能仍是“忠实”但并非真实；失败案例中部分错误源自KG信息不足。
- **复杂问题与长路径**：跳数`L`增大时，Trie构建的时间和空间开销显著上升。论文提到可结合问题分解策略，但尚未实现。
- **LLM推理能力局限**：即使在约束下，LLM仍可能生成与问题无关的合法路径，导致答案错误（如案例1）。
- **领域泛化差异**：在医学KG上提升较小，说明对高度专业化知识的泛化能力仍有待加强。
- **实验细节**：未报告跨多次运行的不确定性（如随机种子影响），消融实验仅使用ChatGPT作为通用LLM，未探索其他配置。

（完）
