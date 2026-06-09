---
title: Can Knowledge-Graph-based Retrieval Augmented Generation Really Retrieve What You Need?
title_zh: 基于知识图谱的检索增强生成真的能检索到你需要的内容吗？
authors: "Junchi Yu, Yujie Liu, Jindong Gu, Philip Torr, Dongzhan Zhou"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=po0eyoYFUa"
tags: ["query:graph-llm"]
score: 9.0
evidence: 利用知识图谱通过检索增强生成提升LLM，解决检索准确性与多样性问题
tldr: 针对现有基于知识图谱的检索增强生成方法难以从文本丰富图谱中检索准确多样信息的问题，GraphFlow 框架通过可训练的过程奖励模型对检索过程进行对齐，无需昂贵的过程级监督信号即可高效检索满足复杂查询需求的知识。该方法为 LLM 与知识图谱的深度融合提供了实用方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-po0eyoyfua/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 988, \"height\": 362, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-po0eyoyfua/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1234, \"height\": 370, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-po0eyoyfua/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1305, \"height\": 732, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-po0eyoyfua/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 632, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-po0eyoyfua/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1447, \"height\": 783, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-po0eyoyfua/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1123, \"height\": 740, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-po0eyoyfua/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1251, \"height\": 715, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-po0eyoyfua/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1138, \"height\": 728, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-po0eyoyfua/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1152, \"height\": 761, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-po0eyoyfua/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1457, \"height\": 653, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-po0eyoyfua/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1402, \"height\": 458, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-po0eyoyfua/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1447, \"height\": 312, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-po0eyoyfua/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1405, \"height\": 264, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-po0eyoyfua/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1185, \"height\": 693, \"label\": \"Table\"}]"
motivation: 现有 KG-RAG 方法在文本丰富知识图谱上检索准确且多样的知识表现不佳，且过程监督信号昂贵难获。
method: 提出 GraphFlow 框架，利用可训练过程奖励模型对齐 KG 检索与查询需求，高效检索准确多样知识。
result: GraphFlow 能有效提升检索质量和多样性，更好满足现实复杂查询。
conclusion: 该框架为知识图谱增强的 LLM 提供了一种高效、可扩展的检索方案，推动了图-语言模型集成。
---

## Abstract
Retrieval-Augmented Generation (RAG) based on knowledge graphs (KGs) enhances large language models (LLMs) by providing structured and interpretable external knowledge.
However, existing KG-based RAG methods struggle to retrieve accurate and diverse information from text-rich KGs for complex real-world queries.
Process Reward Models (PRMs) offer a way to align the retrieval process of KG-based RAG with query-specific knowledge requirements, 
but they heavily rely on process-level supervision signals that are expensive and hard to obtain on KGs.
To address this challenge, we propose GraphFlow, a framework that efficiently retrieves accurate and diverse knowledge required for real-world queries from text-rich KGs.
GraphFlow employs a transition-based flow matching objective to jointly optimize a retrieval policy and a flow estimator.
The flow estimator factorizes the reward of the retrieval outcome into the intermediate retrieval states.
Such reward factorization guides the retrieval policy to retrieve candidates from KGs in proportion to their reward.
This allows GraphFlow to explore high-quality regions of KGs that yield diverse and relevant results. 
We evaluate GraphFlow on the STaRK benchmark, which includes real-world queries from multiple domains over text-rich KGs. 
GraphFlow outperforms strong KG-RAG baselines, including GPT-4o, by 10\% on average in hit rate and recall. 
It also shows strong generalization to unseen KGs, demonstrating its effectiveness and robustness.

---

## 论文详细总结（自动生成）

# 论文总结与分析

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：现有基于知识图谱的检索增强生成方法在处理涉及文本丰富知识图谱的复杂查询时，难以同时保证检索结果的**准确性**和**多样性**。复杂查询不仅需要利用图结构信息，还需要理解节点和边的文本描述（如论文内容、机构信息等），传统方法往往无法有效融合这两类信息，导致检索结果不准确或覆盖不全。
- **背景与动机**：过程奖励模型能够对多步检索过程进行逐步指导，但其训练需要昂贵的过程级监督信号，而在知识图谱上标注每一步的收益（即过程奖励）成本极高且难以获得。因此，论文旨在设计一种无需过程级监督即可将检索结果与查询需求对齐的框架，从而高效地从文本丰富的知识图谱中检索出准确且多样的知识。

## 2. 论文提出的方法论
### 2.1 核心思想
将知识图谱上的检索过程建模为**多步决策问题**，并采用**能量模型**的思想，希望学习一个策略，使检索轨迹被采样的概率与其最终奖励成正比，即 $P(\tau) \propto R(\tau)$。这样既能鼓励对高奖励区域的探索，又能天然地促进多样性。

### 2.2 关键技术细节
- **流程估计与信用分配**：引入 **GFlowNet** 框架，通过训练一个**流程估计器**为每个中间状态分配非负的流量值。利用**详细平衡条件**：
  \[
  F(s_t) \cdot P(s_{t+1} \mid s_t) = F(s_{t+1}) \cdot P_B(s_t \mid s_{t+1})
  \]
  将轨迹的终端奖励隐式分解到中间步骤，从而为策略提供过程级指导，而无需显式标注过程奖励。
- **局部探索策略**：为避免在整个知识图谱上执行详细平衡造成的计算低效，仅仅在采样轨迹的每个非终止状态处进行局部探索，即随机选择若干邻居节点作为候选下一步状态，并基于这些局部转移计算损失函数。
- **终止条件**：引入特殊的自循环动作，若策略选择该动作，则表示当前文档已足够回答查询，轨迹终止；否则继续探索，使智能体学会自适应停止。
- **LLM实现**：用预训练语言模型作为骨干编码器，配合策略头和流程头，分别输出转移概率（通过softmax）和状态的流程对数值。采用 LoRA 进行参数高效微调。

### 2.3 公式或算法流程说明
- **损失函数（Detailed Balance with Local Exploration, DBLE）**：
  \[
  \mathcal{L}_{\text{DBLE}}(s_t) = \sum_{i=0}^{k} \left[ \log F(s_t) - \log F(s'_{t+1,i}) + r_\theta(s_t, a'_{t,i}) - \log \sum_{i=0}^{k} e^{r_\theta(s_t, a'_{t,i})} \right]^2
  \]
  其中 $r_\theta(s,a)$ 为学习的流程奖励函数，$F$ 为流程估计值，边界条件 $\log F(s_0)=\log F(s_T)=1$。
- **训练过程**：先在训练集上收集从起点到目标节点的有效轨迹，提取状态转移对，并构建局部探索动作，然后通过最小化上述损失联合优化策略网络和流程估计器。

## 3. 实验设计
### 3.1 数据集与场景
- 采用 **STaRK 基准**，包含三个真实世界领域的文本丰富知识图谱：
  - **STaRK-AMAZON**：电商图，节点含详细产品信息，边表示产品属性与共购关系。
  - **STaRK-MAG**：学术图，节点含作者、机构、论文等信息。
  - **STaRK-PRIME**：生物医学图，节点含药物、疾病、基因等详细描述。
- **任务**：针对复杂自然语言查询，从图中检索准确、多样的支持文档。

### 3.2 对比方法
- **检索型方法**：DenseRetriever (基于SentenceBERT)、G-Retriever (PCST算法)、SubgraphRAG (可学习子图检索模块)。
- **智能体型方法**：ToG (分别基于LLaMA3-8B和GPT-4o)、有监督微调、过程奖励模型。
- 所有智能体方法均进行20次检索，评估前20个结果的准确性和多样性，并报告重排序后的性能。

### 3.3 评估指标
- **准确性**：Hit@1、Hit@5、MRR。
- **多样性**：Recall@20 (R@20)、去重Recall@20 (D-R@20)。
- **检索质量量化**：步骤级和答案级的语义困惑降低分数 (ΔSeper)。

## 4. 资源与算力
- 文中明确提到实验使用了 **8/16 块 NVIDIA A800-SXM4-80GB GPU** 和 **56 个 Intel Xeon Platinum 8336C CPU**。
- 训练GraphFlow的详细配置在附录表格中给出（如LoRA秩、学习率、epoch数等），但未明确给出总训练时长。

## 5. 实验数量与充分性
- **主要实验**：在三个数据集上对比了检索型与智能体型共8种方法，报告了准确率、召回率、多样性等多维度指标，并分别给出了无重排序和重排序的设置。
- **附加实验**：量化检索质量的ΔSeper分析、跨域泛化实验（在不同数据集间迁移训练）、不同难度级别（基于检索目标数量）的性能分析。
- **消融与分析**：通过对比GraphFlow、SFT、PRM的公式差异，解释了GraphFlow的优势；展示了训练动态曲线、硬样本上的表现等。
- 整体来看，实验设计全面，覆盖了多个领域、多种基线、多种指标，并且考虑了泛化性和难度分层，具有较强的充分性和客观性；所有基线均基于统一的后处理（如寻找种子节点）以保证公平对比。

## 6. 论文的主要结论与发现
- **GraphFlow显著提升了复杂查询下的检索准确性和多样性**：在大部分指标上超过所有基线，包括使用GPT-4o的ToG，平均提升约10%。
- **无需过程级监督，仅靠结果奖励即可实现有效的信用分配**：GraphFlow通过流程估计隐式学习到逐步的指导信号，避免了昂贵的过程标注。
- **具有良好的泛化能力**：在未知领域的知识图谱上仍然能够有效检索，相比于过拟合到似然最大化的SFT和PRM，GraphFlow的客观性更强。
- **尤其在检索目标多样**（超过15个）的困难查询上，GraphFlow的优势最为明显，证明其能够覆盖更广泛的相关文档。

## 7. 优点
- **问题新颖性**：首次在文本丰富知识图谱的复杂RAG中引入GFlowNet来解决多样性-准确性平衡问题，并避免过程监督。
- **方法论创新**：提出的DBLE损失函数结合局部探索，将GFlowNet适配到知识图谱的多跳检索场景，计算可行且有效。
- **实验全面**：在多个领域、多种指标、多种设置下进行验证，并分析了泛化性和难度分层，结论可信。
- **实现高效**：采用LoRA微调，只需轨迹级奖励，工程上易于部署。

## 8. 不足与局限
- **泛化实验有限**：仅评估了跨两个新域的泛化，可能不足以充分说明跨任意领域的鲁棒性（作者自述为限制）。
- **计算依赖**：尽管已经采用局部探索，但图遍历和LLM编码的计算开销依然较大，扩展到超大规模知识图谱可能面临挑战。
- **终止条件自循环**：虽然使策略能自适应停止，但在训练早期可能导致策略过早终止，影响探索效率，文中未深入分析该问题。
- **流程估计的稳定性**：GFlowNet的训练有时对超参数敏感，论文未展示不同超参数（如局部探索数k）的敏感性分析。
- **依赖初始节点识别**：方法需要预先找到合理的起点节点，其性能可能受限于初始节点定位的质量，文中未讨论该前提的失效影响。

---
（完）
