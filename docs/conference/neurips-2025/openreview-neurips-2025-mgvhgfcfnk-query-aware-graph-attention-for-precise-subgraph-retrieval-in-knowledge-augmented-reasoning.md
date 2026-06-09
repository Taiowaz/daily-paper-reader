---
title: Query-Aware Graph Attention for Precise Subgraph Retrieval in Knowledge-Augmented Reasoning
title_zh: 查询感知图注意力用于知识增强推理中的精确子图检索
authors: "Yuanye Xu, Yue Zhang, Ning Fu"
date: 2025-05-11
pdf: "https://openreview.net/pdf?id=MGvhGFCFNK"
tags: ["query:graph-llm"]
score: 8.0
evidence: 图注意力从知识图谱检索子图以增强LLM推理
tldr: 现有知识图谱增强的大语言模型在复杂推理中难以精确检索相关子图。本文提出查询感知图注意力框架，动态结合查询语义和关系信息，精准检索图证据。在多个多跳问答数据集上，该方法显著提升了LLM的事实准确性，推动了知识增强推理的发展。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-mgvhgfcfnk/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1169, \"height\": 786, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mgvhgfcfnk/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1447, \"height\": 861, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mgvhgfcfnk/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1445, \"height\": 887, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mgvhgfcfnk/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1443, \"height\": 1340, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mgvhgfcfnk/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1448, \"height\": 864, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mgvhgfcfnk/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1447, \"height\": 900, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mgvhgfcfnk/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1445, \"height\": 956, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-mgvhgfcfnk/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 878, \"height\": 283, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mgvhgfcfnk/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1445, \"height\": 777, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mgvhgfcfnk/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 731, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mgvhgfcfnk/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 725, \"height\": 397, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mgvhgfcfnk/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 732, \"height\": 172, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mgvhgfcfnk/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1069, \"height\": 405, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mgvhgfcfnk/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1375, \"height\": 1296, \"label\": \"Table\"}]"
motivation: 现有KG-RAG方法难以动态准确地检索与查询相关的图证据。
method: 设计查询感知图注意力机制，联合利用查询语义和关系信息进行子图检索。
result: 在多跳问答任务上显著提升LLM的事实准确性。
conclusion: 该框架为知识图谱与语言模型的深度集成提供了新思路。
---

## Abstract
In recent years, Retrieval-Augmented Generation (RAG) has demonstrated great potential in enhancing the factual accuracy of large language models (LLMs) in open-domain question answering. Incorporating knowledge graphs (KGs) as external knowledge sources into the RAG paradigm is a promising direction. However, KG-RAG systems for complex multi-hop reasoning tasks still face significant challenges in precisely retrieving structured evidence highly relevant to the query. Existing approaches struggle to dynamically and accurately retrieve graph-based evidence by effectively leveraging query semantics and relational information. To address these challenges, we propose a novel framework called Query-aware Subgraph Retrieval Augmented Generation (QSRAG), centered around a new attention-based architecture termed Query-Relational Graph Attention Network (QR-GAT). QR-GAT is a graph attention mechanism that learns expressive representations of triples by capturing intricate interactions between the query context and relation types. Based on these representations, a scoring module assigns fine-grained relevance scores to triples in the KG, enabling precise subgraph retrieval for downstream reasoning. These structured evidence subgraphs, enriched with confidence scores, are then provided to an LLM to enhance its reasoning capability. Extensive experiments on two widely-used multi-hop Knowledge Graph Question Answering (KGQA) datasets, WebQSP and CWQ, demonstrate that our approach achieves state-of-the-art retrieval performance, particularly excelling in identifying complex multi-hop evidence. KGQA results further show that QSRAG delivers state-of-the-art or competitive performance on both datasets. Our work highlights the effectiveness of query-aware graph attention for accurate structured evidence retrieval, and its potential to enhance knowledge-augmented reasoning with large language models.

---

## 论文详细总结（自动生成）

下面是按照要求生成的详细中文总结。

## 1. 论文的核心问题与整体含义

- **研究背景与动机**：检索增强生成（RAG）能有效提升大语言模型（LLM）的事实准确性，将知识图谱（KG）作为外部知识源是重要方向。然而，在复杂的多跳推理任务中，现有知识图谱增强检索增强生成（KG‑RAG）系统面临三个核心难题：
  - 多跳结构中的相关证据难以精确识别，常受无关邻居和冗余信息的干扰。
  - 查询语义与图结构的交互建模不足，图检索或图神经网络方法未能动态融入查询意图。
  - 检索噪声高、LLM上下文利用效率低，无关三元组稀释有用信息，迭代调用 LLM 也增加推理延迟。
- **整体含义**：该工作致力于通过查询感知和关系引导的图注意力机制，实现精细的、动态的三元组评分与子图检索，从而为下游 LLM 提供高质量的、聚焦的结构化证据，增强复杂多跳知识图谱问答的能力。

## 2. 论文提出的方法论

- **核心思想**：构建一个名为 **QSRAG（Query-aware Subgraph Retrieval Augmented Generation）** 的两阶段框架，其核心是一个新的注意力架构——**查询‑关系图注意力网络（QR‑GAT）**。该网络通过融合全局查询语义和显式的关系类型，在消息传递过程中动态调节对实体和关系的注意力，从而实现三元组级别的精细评分和精确子图检索。
- **关键技术细节与流程**：
  - **实体与关系编码**：使用预训练文本编码器（gte-large-en-v1.5）获得实体、关系和问题的语义嵌入。
  - **节点初始化**：将实体嵌入、查询嵌入和主题实体指示符拼接，经 Dropout 后作为初始节点表示。
  - **QR‑GAT 注意力计算**：
    - 每一层对源节点和目标节点进行线性投影。
    - 注意力系数由两部分构成：
      - 基础结构注意力（base）：基于源、目标节点表示和关系嵌入。
      - 查询‑关系增强注意力（plus）：基于查询向量与关系向量的点积。
    - 最终注意力为标准 softmax 归一化后的两项之和。
  - **双向编码**：使用双向 QR‑GAT（BiQR‑GAT）同时编码正向和反向边，最终实体表示由两个方向的拼接得到。
  - **三元组评分**：利用头实体、关系、尾实体表示和查询向量，通过两层 MLP 计算三元组相关性分数。
  - **训练与推理**：
    - 检索器作为二分类器训练，使用二元交叉熵损失，正例为从主题实体到答案实体最短路径上的三元组，负例为其他三元组。
    - 推理时对所有候选三元组打分，选取 Top‑k 形成子图。
  - **推理阶段**：将检索到的 Top‑k 三元组及其置信度分数格式化为文本提示，注入 LLM（Llama、GPT-4o-mini、GLM-4-Air 等）进行上下文学习，生成最终答案。无需对 LLM 进行微调。

## 3. 实验设计

- **数据集**：使用两个广泛采用的多跳知识图谱问答基准：
  - **WebQuestionsSP（WebQSP）**：4,737 个问题，最多两跳推理。
  - **Complex WebQuestions（CWQ）**：34,699 个问题，高组合性和多跳要求。两者均构建在 Freebase 上，沿用前置工作（如 RoG）的数据预处理与划分。
- **评估指标**：
  - 检索阶段：三元组召回率（Triplet Recall@k）、答案召回率（Answer Recall@k）。
  - 问答阶段：Micro F1、Macro F1、Hit、Hit@1。
- **对比基准**：对比了多种代表性方法，包括 SR+NSM w/ E2E、Retrieve‑Rewrite‑Answer、RoG、G‑Retriever、GNN‑RAG 以及 SubgraphRAG。其中 SubgraphRAG 为最主要的对比对象。

## 4. 资源与算力

- 文中明确提到使用 **K100‑Ai 集群** 完成全部训练和推理过程。
- 除集群名称外，未详细说明 GPU 型号、数量、训练时长等具体算力配置。因此，算力细节处于不完整披露状态。

## 5. 实验数量与充分性

- **实验组数概览**：
  - 在 WebQSP 和 CWQ 两个数据集上进行了检索和推理的主实验。
  - 检索性能受 Top‑k 数量影响的实验（k 从 50 到 500，共 6 组）。
  - 推理性能受 Top‑k 数量影响的实验（k 从 50 到 500，共 6 组）。
  - 检索器消融实验（对比 base 与 plus 注意力）。
  - 不同 LLM 推理实验（Llama、GPT-4o‑mini、GLM-4‑Air 以及不同 k 值的组合，共多组）。
  - 置信度过滤阈值实验（对比无置信度、使用置信度、以及 4 种不同阈值下的 GLM-4‑Air，共 7 个子配置）。
  - 附录包含多个问答示例与提示模板。
- **实验充分性与公平性**：
  - 实验覆盖了检索和端到端问答两个层面，并从 Top‑k 数量、置信度利用方式、注意力模块贡献等多个角度进行深入分析，总体较为充分。
  - 与近年代表性方法（尤其是 SubgraphRAG）进行全面比较，并复现了部分基线结果以对齐设置。
  - 不足之处：未报告误差条或统计显著性检验，部分结论仅基于单一测试集分数。

## 6. 论文的主要结论与发现

- QR‑GAT 检索器在 WebQSP 和 CWQ 上均取得最优的三元组召回率（Triplet Recall@k），尤其在 CWQ 上显著超越 SubgraphRAG（+11.3%）。
- 在问答性能上，QSRAG 结合不同 LLM 均获得领先或具有竞争力的结果，证明了精准结构化证据检索能够有效提升 LLM 的多跳推理能力。
- 置信度分数为 LLM 推理提供了细粒度的证据整合信号，简单置信度过滤反而可能丢弃有效信息，投放全部 Top‑k 加置信度的策略最优。
- 查询‑关系增强注意力机制（αplus）是实现高精度检索的关键，移除该部分导致检索性能明显下降。

## 7. 优点

- **方法创新性**：提出查询‑关系图注意力网络（QR‑GAT），将查询语义和关系类型有机地融入 GNN 的注意力计算中，实现了动态、细粒度的三元组评分，填补了现有图检索方法中缺乏查询感知能力的空白。
- **即插即用的推理方式**：检索到的子图直接作为 LLM 提示输入，无需微调 LLM，保持模型的通用性和可解释性。
- **实验分析深入**：从检索、推理两个阶段出发，对 Top‑k 选择、注意力组件、置信度使用方法等进行了多维度的消融和影响分析，提供了丰富的实践洞见。
- **性能提升显著**：在标准数据集上取得了目前最优的检索性能，且问答结果与当前领先方法持平甚至超越。

## 8. 不足与局限

- **统计显著性未报告**：所有结果均未提供误差棒或显著性检验，难以判断性能差异的稳定性。
- **数据与计算可复现性细节不足**：虽提及“K100‑Ai 集群”，但未给出 GPU 型号、数量、训练耗时等信息，复现门槛较高。
- **噪声累积问题**：分析表明，增大 Top‑k 虽提升检索召回率，但会引入噪声从而损害推理性能，该方法仍对检索规模敏感。
- **应用场景局限**：实验仅在 WebQSP 和 CWQ 两个 Freebase 数据集上进行，向其他大规模知识图谱或领域专有图的泛化性尚未验证。
- **依赖嵌入质量**：初始实体和关系嵌入依赖预训练文本编码器，其覆盖度和语义质量可能会影响最终检索效果。

（完）
