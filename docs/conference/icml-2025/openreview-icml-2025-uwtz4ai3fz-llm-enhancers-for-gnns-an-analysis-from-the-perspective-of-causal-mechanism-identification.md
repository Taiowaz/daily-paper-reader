---
title: "LLM Enhancers for GNNs: An Analysis from the Perspective of Causal Mechanism Identification"
title_zh: LLM增强器用于GNN：因果机制识别视角的分析
authors: "Hang Gao, Huang Wenxuan, Fengge Wu, Zhao Junsuo, Changwen Zheng, Huaping Liu"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=UWTz4ai3FZ"
tags: ["query:graph-llm"]
score: 9.0
evidence: 通过因果干预分析LLM增强的GNN节点特征
tldr: 针对LLM作为GNN特征增强器优化节点表示的方法缺乏深入理解的问题，本文构建可控因果的合成图数据集，通过交换干预实验探究LLM与GNN协同工作的深层机制。结果表明，LLM增强器通过捕获语义因果性显著提升GNN性能，该发现为图表示学习与LLM融合提供了新的理论支撑。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-uwtz4ai3fz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 454, \"height\": 310, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uwtz4ai3fz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1779, \"height\": 507, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uwtz4ai3fz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 868, \"height\": 565, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uwtz4ai3fz/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 622, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uwtz4ai3fz/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1641, \"height\": 806, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uwtz4ai3fz/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 787, \"height\": 716, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uwtz4ai3fz/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1432, \"height\": 310, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uwtz4ai3fz/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1261, \"height\": 442, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uwtz4ai3fz/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 377, \"height\": 332, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uwtz4ai3fz/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1432, \"height\": 711, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uwtz4ai3fz/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1432, \"height\": 763, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uwtz4ai3fz/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1720, \"height\": 639, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uwtz4ai3fz/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1256, \"height\": 704, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uwtz4ai3fz/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1527, \"height\": 723, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uwtz4ai3fz/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1594, \"height\": 879, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-uwtz4ai3fz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1778, \"height\": 428, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uwtz4ai3fz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 709, \"height\": 192, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uwtz4ai3fz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 770, \"height\": 149, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uwtz4ai3fz/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 767, \"height\": 185, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uwtz4ai3fz/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 789, \"height\": 139, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uwtz4ai3fz/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1677, \"height\": 385, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uwtz4ai3fz/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 448, \"height\": 572, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uwtz4ai3fz/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1701, \"height\": 2262, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uwtz4ai3fz/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1505, \"height\": 584, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uwtz4ai3fz/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 820, \"height\": 115, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uwtz4ai3fz/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 722, \"height\": 182, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uwtz4ai3fz/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 725, \"height\": 138, \"label\": \"Table\"}]"
motivation: 利用LLM提升GNN节点表示的方法尽管有效，但其底层机制尚不明确，限制了进一步改进。
method: 构建可控因果的合成图数据集，采用交换干预方法分析LLM增强器与GNN的因果作用。
result: 实验揭示了LLM特征增强通过捕捉语义因果性提升GNN性能，并验证了方法的合理性。
conclusion: 该分析加深了对LLM-GNN融合的理解，为未来集成图神经网络与语言模型提供了理论基础。
---

## Abstract
The use of large language models (LLMs) as feature enhancers to optimize node representations, which are then used as inputs for graph neural networks (GNNs), has shown significant potential in graph representation learning. However, the fundamental properties of this approach remain underexplored. To address this issue, we propose conducting a more in-depth analysis of this issue based on the interchange intervention method. First, we construct a synthetic graph dataset with controllable causal relationships, enabling precise manipulation of semantic relationships and causal modeling to provide data for analysis. Using this dataset, we conduct interchange interventions to examine the deeper properties of LLM enhancers and GNNs, uncovering their underlying logic and internal mechanisms. Building on the analytical results, we design a plug-and-play optimization module to improve the information transfer between LLM enhancers and GNNs. Experiments across multiple datasets and models validate the proposed module.

---

## 论文详细总结（自动生成）

## 一、论文核心问题与整体含义

- **研究背景**：利用大语言模型（LLM）作为特征增强器，生成语义丰富的节点表示后再输入图神经网络（GNN），是当前图表示学习中的热门范式，在诸多任务中取得了优异效果。
- **核心问题**：这一“LLM增强器+GNN”框架的基础性质、深层逻辑和内部工作机制尚缺乏系统研究，两个黑盒模块之间的信息传递与因果建模能力未被透彻理解。
- **整体含义**：本工作旨在填补这一空白，从因果机制识别的角度量化分析该范式，揭示LLM增强器和GNN各自的角色，并在此基础上设计即插即用的优化模块以提升整体性能。

## 二、方法论

### 1. 核心思想
- 引入因果推断中的**交换干预方法**，将神经网络视作低层模型，数据合成逻辑作为高层因果模型。
- 通过替换两个不同输入下模型内部变量值，比较高层与低层模型的输出差异，寻找能够与高层因果变量对齐的隐层表示，从而揭示模型内部逻辑。

### 2. 技术关键点
- **可控因果语义图数据集（CCSG）**：
  - 基于 Wikipedia 条目构建，涵盖 3 大主类、15 个子类共 5660 个条目。
  - 可主动控制节点属性（语义或随机）、节点关联（类别、子类、引用关系）和拓扑结构（网格、环、树、星型、完全图、二分图等）。
  - 支持注入预定义的多阶因果关系，提供可验证的高层因果模型 \(h(\cdot)\)。
- **交换干预分析框架**：
  - 对高层因果模型 \(h(\cdot)\) 执行干预：选取变量 \(Z_h\)，将样本 \(G_{\text{diff}}\) 下的 \(Z_h\) 值置换到 \(G_{\text{orig}}\) 中，得到输出 \(\text{INTINV}(h, G_{\text{orig}}, G_{\text{diff}}, Z_h)\)。
  - 对低层模型 \(f(\cdot)\) 做类似干预，选取内部变量 \(Z_f\)，输出 \(\text{INTINV}(f, G_{\text{orig}}, G_{\text{diff}}, Z_f)\)。
  - 最小化互换干预损失：
    \[
    L_{\text{II}} = \frac{1}{|G|^2} \sum_{G_{\text{orig}}\in G} \sum_{G_{\text{diff}}\in G} D\big(\text{INTINV}(h, \dots), \text{INTINV}(f, \dots)\big),
    \]
    其中 \(D\) 为交叉熵等度量。
  - 理论上证明（定理 3.2、推论 3.3）当 \(L_{\text{II}}\) 达到最小时，找到的 \(Z_f\) 与 \(Z_h\) 具有相同的总因果效应，保证了分析的有效性。
- **分析实验设计**：
  - **节点级任务**：定义高层模型 \(h_{\text{node}} = h_{\text{node},3} \circ h_{\text{node},2} \circ h_{\text{node},1}\)，分别处理单节点特征、节点间关系与目标节点输出。
  - **图级任务**：\(h_{\text{graph}} = h_{\text{graph},3} \circ h_{\text{graph},2} \circ h_{\text{graph},1}\)，依次处理子结构特征、拓扑结构类别和最终图标签。
  - 通过在不同 GNN 层中寻找使 \(L_{\text{II}}\) 最小的隐变量位置，观察高层次变量在 GNN 中的对应层。
- **注意力传输模块（AT）**：
  - 针对 LLM 增强器输出中 token 特征位置影响大的观察，设计 AT 模块改善信息传递。
  - 使用 \(q\) 个不同的提示得到 \(q\) 组特征集，每组选取 \(m\) 个特征向量，通过 Transformer 编码器生成注意力分数矩阵，计算平均注意力权重，对所有特征向量加权求和得到最终节点表示。
  - 前 \(\delta\) 个 epoch 训练提示选择，之后固定最佳提示，实现即插即用优化。

## 三、实验设计

### 数据集与基准
- **合成数据集**：CCSG（含节点级和图级可控因果配置）。
- **真实数据集**：Cora、Pubmed、Instagram，用于验证 AT 模块。
- **对比参照**：Citeseer、Wiki‑CS、Synthetic Graph、Spurious‑Motif、CRCG 等（用于说明 CCSG 的可控性优势）。

### 模型与组合
- **LLM 增强器**：Llama2（含带提示/不带提示版本）、Qwen2、Llama3，参数冻结。
- **GNN 骨干**：GCN、GAT、GraphSAGE，不同层数（2~10）和隐藏维度（16~2048）。
- **对比方式**：分析实验探索最优 \(L_{\text{II}}\) 与 GNN 层、隐藏维度、LLM 类型、特征 token 位置的关系；AT 模块实验中对比 w/o AT 和 w/ AT 的准确率。

## 四、资源与算力
- 所有实验在 **单块 A100 GPU** 上完成，操作系统 Ubuntu 20.04。
- 训练超参数：学习率 0.001，总 epoch 数 200；LLM 部分仅推理不微调。
- 论文未具体说明单次训练的具体耗时或总 GPU 小时数。

## 五、实验数量与充分性
- **分析实验组数多**：节点级、图级分别进行；改变 GNN 层数（5 种）、隐藏维度（4 种）、LLM 类型（4 种）、特征 token 位置（10 种）；并对比不同数据集（额外补充 OGBN‑Arxiv 和随机特征实验）。
- **消融与超参数实验**：AT 模块中不同提示数量 \(q\)（1~4）的性能比较。
- **模型组合丰富**：3 种 LLM × 3 种 GNN，共 9 种搭配，每种均进行 w/o AT 和 w/ AT 的对比。
- **评价**：实验覆盖面很广，不仅包含性能验证，还在多个尺度上进行机制探究，整体较为充分、客观、公平。但真实数据集的规模有限，且未在超大图上进行扩展测试。

## 六、主要结论与发现
1. **经验发现 1**：在固定参数 LLM 增强器下，LLM 输出的特征主要承担节点级和原始数据级的信息表示功能。
2. **经验发现 2**：GNN 内部呈现出相对稳定的逻辑模式，即使模型尺度变化，偶数层对齐效果始终差于奇数层，最终层对齐效果最差，表明 GNN 结构扩展并未增强其因果关系建模能力。
3. **经验发现 3**：基于 \(L_{\text{II}}\) 的分析能部分反映模型能力，更低的最优 \(L_{\text{II}}\) 通常对应更高的下游任务准确率。
4. **AT 模块有效性**：该模块能够显著提升多种 LLM 与 GNN 组合在 Cora、Pubmed 和 Instagram 上的节点分类性能，证明了优化 LLM‑GNN 信息传递的重要性。

## 七、优点
- **理论扎实**：利用因果干预方法，提供严格的理论保证（定理 3.2 ~ 3.5），确保分析的可信度。
- **数据集创新**：CCSG 具有可控的因果和语义关系，适用于深层次的分析，远超传统合成数据集。
- **分析维度系统**：从节点级、图级，不同模型规模和特征位置多角度剖析，结论具有较强普适性。
- **即插即用优化**：AT 模块简单有效，不改变主干网络结构，易于集成到现有框架。

## 八、不足与局限
- **合成与真实数据的差距**：分析主要在 CCSG 上进行，虽然真实数据集上也验证了优化模块，但因果分析本身依赖已知的真实因果模型，难以直接推广到无标注因果结构的真实场景。
- **LLM 使用受限**：LLM 参数冻结，可能未能完全发挥 LLM 的可塑性；分析结果对微调场景是否仍然成立未知。
- **AT 模块计算开销**：引入多提示生成和额外 Transformer 编码器，增加了推理成本，论文未详细讨论效率问题。
- **任务类型单一**：主要聚焦节点分类，未覆盖链路预测、图分类等其他图任务；数据集规模中等，对大规模图（如千万级节点）的可扩展性未评估。
- **模型种类限制**：仅使用了 3 种 GNN 和 3 种 LLM，对更多类型的 LLM 或 GNN（如异构图网络）是否等效有待验证。

（完）
