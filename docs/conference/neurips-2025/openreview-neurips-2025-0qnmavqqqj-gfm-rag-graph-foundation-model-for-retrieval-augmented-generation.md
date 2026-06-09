---
title: "GFM-RAG: Graph Foundation Model for Retrieval Augmented Generation"
title_zh: GFM-RAG：面向检索增强生成的图基础模型
authors: "Linhao Luo, Zicheng Zhao, Gholamreza Haffari, Dinh Phung, Chen Gong, Shirui Pan"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=0QNmAvQQqj"
tags: ["query:graph-llm"]
score: 9.0
evidence: 将图基础模型集成到大语言模型的检索增强生成中以支持复杂推理
tldr: 现有的检索增强生成方法难以获取知识间的复杂关系，导致复杂推理受限。GFM-RAG提出基于图基础模型的RAG框架，通过多级图索引、任务感知检索和自适应图融合，有效建模知识关联并抑制噪声。在多个推理基准上，GFM-RAG相比现有GraphRAG方法显著提升了答案准确性与事实性，验证了图基础模型在增强LLM推理中的价值。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-0qnmavqqqj/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 760, \"height\": 301, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0qnmavqqqj/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1454, \"height\": 1101, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0qnmavqqqj/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 658, \"height\": 532, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0qnmavqqqj/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 708, \"height\": 548, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0qnmavqqqj/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1399, \"height\": 544, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0qnmavqqqj/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1399, \"height\": 490, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-0qnmavqqqj/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1313, \"height\": 903, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0qnmavqqqj/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1315, \"height\": 595, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0qnmavqqqj/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1174, \"height\": 446, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0qnmavqqqj/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1311, \"height\": 795, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0qnmavqqqj/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1305, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0qnmavqqqj/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1317, \"height\": 475, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0qnmavqqqj/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1178, \"height\": 1029, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0qnmavqqqj/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1120, \"height\": 295, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0qnmavqqqj/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1334, \"height\": 355, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0qnmavqqqj/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1231, \"height\": 277, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0qnmavqqqj/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1131, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0qnmavqqqj/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 589, \"height\": 262, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0qnmavqqqj/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1221, \"height\": 339, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0qnmavqqqj/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1452, \"height\": 219, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0qnmavqqqj/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 860, \"height\": 301, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0qnmavqqqj/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 984, \"height\": 338, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0qnmavqqqj/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 736, \"height\": 142, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0qnmavqqqj/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1263, \"height\": 357, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0qnmavqqqj/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 650, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0qnmavqqqj/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 568, \"height\": 225, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0qnmavqqqj/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1132, \"height\": 336, \"label\": \"Table\"}]"
motivation: 现有RAG难以捕捉知识间复杂关系，图增强方法存在噪声与不完整。
method: 提出GFM-RAG，利用图基础模型实现多级图索引、任务感知检索与图融合增强。
result: 在多个推理基准上，GFM-RAG显著优于现有GraphRAG方法，答案更准确。
conclusion: GFM-RAG展示了图基础模型在增强LLM复杂推理中的巨大潜力。
---

## Abstract
Retrieval-augmented generation (RAG) has proven effective in integrating knowledge into large language models (LLMs). However, conventional RAGs struggle to capture complex relationships between pieces of knowledge, limiting their performance in intricate reasoning that requires integrating knowledge from multiple sources. Recently, graph-enhanced retrieval augmented generation (GraphRAG) builds a graph structure to explicitly model these relationships, enabling more effective and efficient retrievers. Nevertheless, its performance is still hindered by the noise and incompleteness within the graph structure. To address this, we introduce GFM-RAG, a novel graph foundation model (GFM) for retrieval augmented generation. GFM-RAG is powered by an innovative graph neural network that reasons over graph structure to capture complex query-knowledge relationships. The GFM with 8M parameters undergoes a two-stage training process on large-scale datasets, comprising 60 knowledge graphs with over 14M triples and 700k documents. This results in impressive performance and generalizability for GFM-RAG, making it the first graph foundation model applicable to unseen datasets for retrieval without any fine-tuning required. Extensive experiments on three multi-hop QA datasets and seven domain-specific RAG datasets demonstrate that GFM-RAG achieves state-of-the-art performance while maintaining efficiency and alignment with neural scaling laws, highlighting its potential for further improvement.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义

- **核心问题**：传统检索增强生成（RAG）将文档视为独立片段，难以捕捉知识之间复杂的多跳关联，限制了需要跨文档整合信息的多步推理任务的表现。现有图增强 RAG（GraphRAG）虽然在文档间显式建模关系，但面临两类挑战：（1）依赖图结构的算法（如PageRank）受限于图的噪声和不完整性；（2）基于图神经网络（GNN）的方法缺乏泛化能力，需要在新数据集上从头训练。
- **整体含义**：本文旨在构建一个面向 RAG 的**图基础模型（Graph Foundation Model, GFM）**，通过在大规模、多样化的知识图谱上进行预训练，使模型具备在未见数据集上直接进行多跳检索的能力，无需特定领域微调。GFM-RAG 首次将图基础模型范式与 RAG 深度融合，旨在实现更高效、通用且符合神经缩放定律的复杂推理增强。

### 2. 论文提出的方法论

- **核心思想**：采用“知识图谱索引（KG-index）”结构化文档知识，并用一个查询依赖的图神经网络作为通用检索器，通过两阶段大规模训练使其捕获查询-知识间的复杂语义与结构关联，实现单步多跳推理。

- **关键技术细节**
    - **KG-index 构建**：使用大语言模型（GPT-4o-mini）对文档进行开放信息抽取，得到实体、关系及三元组；通过预训练嵌入模型计算实体语义相似度进行实体消歧，补充等价边，形成最终知识图谱。
    - **GFM 检索器（查询依赖 GNN）**：
        - **查询初始化**：将自然语言问题编码为向量，作为问题中提及实体的初始特征。
        - **查询依赖消息传递**：关系嵌入与实体嵌入共享同一语义空间（通过同一句子嵌入模型初始化），每一层用可学习的 MLP 更新关系表示，并采用非参数的 DistMult 生成三元组消息，通过加和聚合更新实体表示。该过程理论上具备多跳逻辑推理能力。
        - **评分**：经过多层传递后，将实体特征通过 MLP 和 Sigmoid 映射为与查询相关的实体相关性得分。
    - **训练过程**：
        1. **自监督知识图谱补全预训练**：掩盖三元组中的头实体或尾实体构造合成查询，训练模型预测缺失实体。
        2. **监督文档检索微调**：使用标注的支持文档中的目标实体进行训练，最大化正实体概率。
        3. 损失函数由二元交叉熵（BCE）和排名损失（Ranking Loss）加权组合而成。
    - **文档排序与生成**：取预测得分最高的 \( T \) 个实体，通过实体-文档倒排索引并加权逆文档频率（IDF）获得文档得分，选取 Top-K 文档送入大语言模型生成最终答案。

### 3. 实验设计

- **数据集与场景**：
    - **多跳问答数据集**：HotpotQA、MuSiQue、2WikiMultiHopQA，用于评估多跳检索与推理能力。
    - **领域特定 RAG 数据集**（共 7 个）：生物医学（PubMedQA）、客服支持（DelucionQA、TechQA、ExpertQA、EManual）、通用知识（MS Marco、HAGRID），用于测试模型作为基础模型的零样本泛化能力。
- **基准对比**：
    - **单步朴素方法**：BM25、Contriever、GTR、ColBERTv2、RAPTOR、Proposition。
    - **图增强方法**：GraphRAG (MS)、LightRAG、HippoRAG、SubgraphRAG、G-retriever。
    - **多步方法**：Adaptive-RAG、FLARE、IRCoT（与不同检索器结合）。
- **评估指标**：检索用 Recall@2（R@2）和 Recall@5（R@5）；问答用完全匹配（EM）和 F1。

### 4. 资源与算力

- **训练环境**：使用 8 块 NVIDIA A100 80GB GPU。
- **训练时长**：预训练阶段约 14 小时，监督微调阶段约 5 小时。
- **模型规模**：GFM 检索器参数量为 8M（不包括冻结的句子嵌入模型）。

### 5. 实验数量与充分性

- **实验数量丰富**：
    - 在 3 个多跳数据集上进行了检索和问答性能对比，涉及的基线方法超过 15 种。
    - 在 7 个领域数据集上进行了零样本泛化性能测试。
    - 包含消融实验：不同句子嵌入模型、训练策略（是否预训练/微调）、损失权重、排序方法、训练数据来源等。
    - 进行了效率分析（检索耗时对比）、神经缩放定律分析、多跳推理路径可解释性分析。
    - 还考察了不同大语言模型用于 KG-index 构建的影响，以及模型在不同层数下的表现。
- **充分性与公平性**：实验覆盖全面，对比方法多样，且均使用相同的测试集分割，消融实验控制了变量，能客观反映各组件的作用，具备较好的说服力。

### 6. 论文的主要结论与发现

- **性能最优**：在三个多跳 QA 数据集上，GFM-RAG 的检索与问答性能均显著超越所有单步、图增强及多步基线方法。
- **高效性**：能在单步检索内完成多跳推理，推理速度远快于多步方法（如 IRCoT），且检索效果更优。
- **泛化能力强**：作为首个图基础模型，无需任何微调即可在 7 个不同领域的 RAG 数据集上取得最优平均性能，并可通过域内微调进一步提升。
- **符合缩放定律**：模型性能随训练数据规模和参数量增加而幂律提升，预示巨大的扩展潜力。
- **可解释性**：GFM 能够给出可解释的多跳推理路径，证明其确实学会了逻辑关联。

### 7. 优点

- **原创性**：首次成功将图基础模型范式拓展至 RAG 领域，实现了跨数据集的零样本节点级检索。
- **高效与有效兼得**：通过单步 GNN 完成多跳推理，避免了迭代检索+LLM 推理的高昂计算开销，同时达到了最高精度。
- **鲁棒性**：对底层句子嵌入模型的选择不敏感，且在不同质量的知识图谱下表现均优于对比方法。
- **可扩展**：验证了缩放定律，为未来将其扩展至更大参数量和更复杂任务提供了理论和实践基础。
- **实验完备**：对比基线全面，消融和泛化实验扎实，包含性能、效率、可解释性多维度分析。

### 8. 不足与局限

- **索引构建开销**：构建 KG-index 依赖大语言模型进行信息抽取，成本较高且耗时，可能限制其在超大规模语料上的快速部署。
- **模型参数量较小**：尽管已有 8M 参数，但与当前动辄数十亿参数的 LLM 相比，图模型容量仍有限，更大规模的图基础模型潜力尚未挖掘。
- **任务覆盖面有限**：目前仅评估了多跳问答和 RAG 召回，对于知识图谱补全、图谱问答等纯图任务的迁移能力未充分验证。
- **依赖外部工具链**：整体流程涉及 OpenIE、实体消歧、LLM 生成等环节，系统较为庞杂，端到端的联合优化仍有空间。
- **文档检索粒度**：采用实体-文档倒排索引在中间层进行信号转换，可能丢失部分细粒度的事实对齐信息。

（完）
