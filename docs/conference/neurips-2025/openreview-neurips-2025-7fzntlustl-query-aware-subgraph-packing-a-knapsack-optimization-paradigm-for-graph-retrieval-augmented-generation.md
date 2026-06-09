---
title: "Query-Aware Subgraph Packing: A Knapsack Optimization Paradigm for Graph Retrieval-Augmented Generation"
title_zh: 查询感知子图打包：图检索增强生成的背包优化范式
authors: "Chenjie Qiu, yongqi luo, Bingfeng chen, Boyan Xu, Ruichu Cai, Zhifeng Hao"
date: 2025-05-12
pdf: "https://openreview.net/pdf?id=7fZNTLuStL"
tags: ["query:graph-llm"]
score: 9.0
evidence: 提出GraphPack，一种向大语言模型注入图结构知识的图检索增强框架
tldr: 针对现有GraphRAG方法使用静态编码、忽略拓扑信息导致冗余的问题，提出将子图选择建模为0-1背包优化，在尺寸预算下联合最大化语义相关性和最小化结构冗余，实验表明所选子图能有效增强LLM的生成效果，推动了图检索增强生成研究。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-7fzntlustl/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1443, \"height\": 642, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7fzntlustl/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1441, \"height\": 697, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7fzntlustl/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 673, \"height\": 447, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-7fzntlustl/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1422, \"height\": 396, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7fzntlustl/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 678, \"height\": 380, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7fzntlustl/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 633, \"height\": 397, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7fzntlustl/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 773, \"height\": 443, \"label\": \"Table\"}]"
motivation: 当前GraphRAG方法依赖扁平相似度检索，忽略拓扑，产生冗余且结构不连贯的证据。
method: 将子图选择建模为0-1背包优化，联合最大化语义相关性和最小化结构冗余。
result: 在多个知识基准上，该方法选择的子图显著提升LLM回答的准确性和信息量。
conclusion: 通过优化子图选择，有效提升了图知识注入LLM的效率和效果。
---

## Abstract
Graph Retrieval‑Augmented Generation (GraphRAG) has recently emerged as a task paradigm for injecting graph‑structured knowledge into large language models (LLMs), yet most existing approaches still rely on flat, similarity‑based retrieval that ignores topology and uses static encoders, producing redundant or structurally incoherent evidence. In this paper, we propose GraphPack, a query‑aware GraphRAG framework that overcomes these limitations by casting subgraph selection as a 0–1 knapsack optimization. For every natural language query, GraphPack packs the most informative subgraph under a size budget by jointly maximizing semantic relevance and minimizing structural redundancy. The selected subgraph is then encoded by a query‑aware graph encoder whose parameters are conditioned on the query, allowing node representations to adapt dynamically to user intent. Extensive experiments on multiple knowledge-intensive graph benchmarks demonstrate that GraphPack achieves state-of-the-art performance, showcasing its strong capability in addressing structural and contextual challenges under supervised learning, cross-domain settings, and zero-shot scenarios.

---

## 论文详细总结（自动生成）

# 论文结构化总结

## 1. 核心问题与整体含义
- **研究背景**：图检索增强生成（GraphRAG）将结构化知识注入大语言模型（LLM），但现有方法普遍依赖**扁平、基于相似度的检索**，忽略图拓扑结构，使用**静态编码器**，导致检索出的图证据往往**冗余、结构不连贯**。
- **核心问题**：如何在子图检索过程中**同时考虑语义相关性与拓扑非冗余性**，并使图编码器**动态适应用户查询意图**。
- **整体含义**：提出 GraphPack，一种**查询感知的 GraphRAG 框架**，通过将子图选择建模为 **0‑1 背包优化**，在预算约束下联合最大化语义价值并最小化结构代价，再将子图经查询条件化编码器处理后注入 LLM，实现更高效、更准确的图知识增强生成。

## 2. 方法论
### 2.1 总体流程
- 对于用户自然语言查询 \(x_q\) 和图 \(G\)，GraphPack 先检索最相关子图 \(G^*\)，再以该子图为条件生成答案 \(y\)，建模为 \(p(y|x_q,G^*)\)。

### 2.2 语义感知子图检索（Knapsack Optimization）
- **图索引**：用冻结的文本编码器（Sentence‑BERT）计算所有节点和边的文本嵌入。
- **锚节点识别**：取与查询嵌入余弦相似度最高的 top‑k 节点作为锚点。
- **背包优化**：
  - 对每个锚点的 n 跳邻域，将节点/边视为物品。
  - **价值函数**：采用排名衰减机制，\(value(e) = max\_score - rank(e)\)，使语义相关性高的元素优先选取。
  - **权重函数**：由元素首次出现的最小跳数决定，\(weight(e) = \min\{n \mid e \in g_{i}^{n}\}\)，近邻权重低、远程权重高，**抑制远距离冗余元素**。
  - 求解目标：在总权重 ≤ 预算 \(C\) 下最大化总价值，使用**动态规划**（0‑1 背包算法）精确求解。
- 最终用查询嵌入作为虚拟节点连接所有选中元素，形成连贯子图。

### 2.3 查询感知图编码器（Query‑LM）
- 在 GNN 消息传递中引入 **Query‑aware Linear Modulation (Query‑LM)**，类似 FiLM 机制。
- 将查询编码为向量 \(h_q\)，通过线性层生成缩放参数 \(\gamma^{(l)}\) 和偏移参数 \(\beta^{(l)}\)，对第 l 层 GNN 的节点表示进行逐通道仿射变换：\(h_v^{(l)} = \gamma_v^{(l)} \odot \tilde{h}_v^{(l)} + \beta_v^{(l)}\)。
- 读出阶段对节点嵌入先做非线性变换再平均池化，得到图级表示 \(h_g\)。

### 2.4 LLM 监督微调与辅助任务
- 将原始查询、子图文本描述和图表示 \(h_g\) 拼接后送入 LLM 解码器。
- 同时设计**辅助图‑文本重建任务**：仅以图表示 \(h_g\) 为条件预测答案，增强图嵌入的可逆性和表达力，不改变模型结构。

## 3. 实验设计
- **数据集**：
  - 节点分类/图分类：Cora、Citeseer、Wikics、Instagram、ogbn‑arxiv。
  - 知识图谱问答：WebQSP、Complex WebQuestions (CWQ)。
- **基准对比方法**：
  - 文本序列化类：OFA、InstructGLM、GraphText、GraphAdapter、LLaGA。
  - GraphRAG 类：G‑Retriever、GRAG。
  - 基座 LLM：Llama‑2‑7B、Mistral‑7B（作为无检索基线）。
- **评估指标**：Acc、F1、Hit@1、Recall（因任务而定）。
- **设定**：监督学习、零样本跨域/跨任务迁移、检索策略影响分析、消融分析。

## 4. 资源与算力
- 文中指出所有训练和实验细节（包括超参数、计算资源）记载于**附录 C**，但提供的文稿中**未给出具体的 GPU 型号、数量、训练时长**。仅提到使用 Llama‑2‑7b 作为基座，并提供代码和补充材料。

## 5. 实验数量与充分性
- **多组实验**：
  - 5 个节点分类数据集 + 2 个知识图谱数据集，覆盖不同类型和规模。
  - 零样本迁移实验：4 组跨域设置（Cora → Wikics/Instagram，CWQ → Wikics/Instagram）。
  - 检索策略对比（表 4），背包容量分析（图 3）。
  - 消融实验：移除排名价值分配、移除 Query‑LM 模块（附录 D.4）。
  - 与 ChatGPT 的定性案例对比（表 3）。
- **充分性与客观性**：实验覆盖多个基准、任务类型和设置，对比方法多样，消融验证关键模块，容量分析有洞察。报告基于 5 次运行的平均结果，具有统计稳定性。未发现明显偏颇或不公。

## 6. 主要结论与发现
- GraphPack 在**所有监督学习基准上取得最优或次优性能**，尤其在知识图谱问答（WebQSP、CWQ）上显著优于现有 RAG 方法。
- 子图检索策略本身（不微调 LLM）即可大幅提升答案质量，**F1 提升 18.61%**，并缓解多实体缺失问题。
- 背包容量分析表明：**过大容量引入噪声，过小则信息不足**，最优容量平衡了丰富度与紧凑性。
- GraphPack 在**零样本跨域和跨任务设定下仍保持优越的泛化能力**。
- 查询感知建模（排名价值分配 + Query‑LM）对性能贡献显著，移除任一部分均导致下降。

## 7. 优点
- **创新性强**：首次将子图选择形式化为 0‑1 背包问题，同时量化语义价值和结构代价。
- **查询动态编码**：引入 Query‑LM 使 GNN 编码过程跟随用户意图动态调整，提升任务针对性。
- **辅助训练任务**：图‑文本重建目标增强了图嵌入的可解释性和独立性，不增加推理成本。
- **实验扎实**：多种数据集、多基线、零样本与消融全面验证，分析深入。

## 8. 不足与局限
- **算力信息缺失**：正文未报告 GPU 资源与训练耗时，难以评估实际开销。
- **对语义嵌入质量敏感**：锚点识别依赖高质量文本嵌入，**噪声或稀疏文本可能降低性能**。
- **下游微调依赖**：仍需针对特定任务进行监督微调，**未实现通用图基础模型**，限制了即插即用能力。
- **实验覆盖**：目前仅涵盖若干标准图数据集，未见对超大规模图（百万级节点）或动态图的实验。
- **偏差风险**：所有数据集均为英文文本图，**多语种或低资源场景未验证**。

（完）
