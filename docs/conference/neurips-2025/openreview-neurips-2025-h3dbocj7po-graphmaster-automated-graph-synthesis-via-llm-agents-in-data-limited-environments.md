---
title: "GraphMaster: Automated Graph Synthesis via LLM Agents in Data-Limited Environments"
title_zh: "GraphMaster: 数据有限环境下通过LLM代理进行自动化图合成"
authors: "Enjun Du, Xunkai Li, Tian Jin, Zhihan Zhang, Rong-Hua Li, Guoren Wang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=h3dbocj7po"
tags: ["query:graph-llm"]
score: 7.0
evidence: 利用LLM代理合成图数据以训练图基础模型
tldr: 图基础模型的训练受限于大规模图语料库的匮乏。本文设计GraphMaster，一个多智能体LLM框架，通过克服上下文窗口和幻觉问题，自动生成带有语义丰富文本属性的图数据。实验表明合成数据能有效提升下游图任务性能，缓解数据稀缺瓶颈。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3dbocj7po/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1449, \"height\": 523, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3dbocj7po/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1407, \"height\": 394, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3dbocj7po/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1355, \"height\": 404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3dbocj7po/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1412, \"height\": 763, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3dbocj7po/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1409, \"height\": 755, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3dbocj7po/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1410, \"height\": 757, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3dbocj7po/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1407, \"height\": 752, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3dbocj7po/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1406, \"height\": 754, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3dbocj7po/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1408, \"height\": 753, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3dbocj7po/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1403, \"height\": 2024, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3dbocj7po/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1355, \"height\": 2439, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3dbocj7po/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1365, \"height\": 1867, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-h3dbocj7po/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1447, \"height\": 390, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h3dbocj7po/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1438, \"height\": 354, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h3dbocj7po/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1438, \"height\": 422, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h3dbocj7po/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1445, \"height\": 439, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h3dbocj7po/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1443, \"height\": 440, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h3dbocj7po/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1445, \"height\": 441, \"label\": \"Table\"}]"
motivation: 大规模图数据稀缺制约图基础模型发展，现有合成方法缺乏语义丰富性。
method: 提出多代理LLM框架GraphMaster，自动生成语义丰富的图数据。
result: 合成数据有效提升下游图任务性能。
conclusion: GraphMaster为图领域数据增强提供了可扩展的解决方案。
---

## Abstract
The era of foundation models has revolutionized AI research, yet Graph Foundation Models (GFMs) remain constrained by the scarcity of large-scale graph corpora. Traditional graph data synthesis techniques primarily focus on simplistic structural operations, lacking the capacity to generate semantically rich nodes with meaningful textual attributes—a critical limitation for real-world applications. While large language models (LLMs) demonstrate exceptional text generation capabilities, their direct application to graph synthesis is impeded by context window limitations, hallucination phenomena, and structural consistency challenges. To address these issues, we introduce \textbf{GraphMaster}—the first multi-agent framework specifically designed for graph data synthesis in data-limited environments. GraphMaster orchestrates four specialized LLM agents (Manager, Perception, Enhancement, and Evaluation) that collaboratively optimize the synthesis process through iterative refinement, ensuring both semantic coherence and structural integrity. To rigorously evaluate our approach, we create new data-limited “Sub” variants of six standard graph benchmarks, specifically designed to test synthesis capabilities under realistic constraints. Additionally, we develop a novel interpretability assessment framework that combines human evaluation with a principled Grassmannian manifold-based analysis, providing both qualitative and quantitative measures of semantic coherence. Experimental results demonstrate that GraphMaster significantly outperforms traditional synthesis methods across multiple datasets, establishing a strong foundation for advancing GFMs in data-scarce environments.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义

- **核心问题**：图基础模型（GFM）的训练严重受限于大规模、高质量图语料库的稀缺。传统图数据合成方法（如边操作、节点插值、图层级混合）仅关注结构层面的简单操作，**无法生成带有丰富语义信息的文本属性节点**，这在文本属性图（TAG）的实际应用中存在明显缺陷。
- **LLM 直接应用的障碍**：大语言模型（LLM）虽然具备强大的文本生成能力，但若直接用于图合成，会面临三方面挑战：
  - 标准上下文窗口无法容纳包含大量文本节点的大规模图；
  - LLM 难以同时保持图结构的拓扑一致性；
  - 缺乏协调的生成容易产生幻觉，无法在全局与局部之间取得平衡。
- **整体含义**：GraphMaster 旨在通过多智能体协作框架，在**数据有限的环境下自动合成兼具语义丰富性和结构完整性的文本属性图**，从而缓解图基础模型的数据瓶颈，为该领域提供首个系统性的 LLM 驱动合成方案。

### 2. 论文提出的方法论

GraphMaster 将图合成形式化为**检索增强生成（RAG）范式**，由四个专门的 LLM 代理（Manager、Perception、Enhancement、Evaluation）通过迭代优化完成。

- **Manager Agent（管理与控制）**
  - 接收环境状态报告，决策当前迭代的增强模式（语义模式或拓扑模式）。
  - 优化多目标效用函数 \( \omega^*_t = \arg\max_{\omega}[\lambda_1 U_{sem} + \lambda_2 U_{struct} + \lambda_3 U_{bal}] \)，权重 \(\lambda\) 自适应更新，以平衡语义一致性、结构完整性和类别均衡。

- **Perception Agent（上下文检索）**
  - 实现 RAG 中的“检索”功能，从输入图中提取可被 LLM 处理的知识子图 \(K_t\) 和环境报告 \(R_t\)。
  - **三步检索流程**：
    1. **语义感知社区识别**：利用语义增强的模块度最大化算法，计算图社区分布。
    2. **模式自适应种子选择**：根据增强模式选择种子社区（语义模式选择小而内聚的社区，拓扑模式优先选择少数类节点）。
    3. **分层随机扩散采样**：使用基于个性化 PageRank（PPR）的模式条件扩散采样，选出代表性节点组成知识子图，规模受限于 LLM 上下文窗口。

- **Enhancement Agent（生成）**
  - 根据知识子图 \(K_t\)、环境报告 \(R_t\) 和增强模式，同时生成新节点属性和连接关系。
  - **语义模式**：采用条件自回归模型 \(P(x_s|K)\) 生成文本属性。
  - **拓扑模式**：基于语义相似度、共同邻居比率和节点度，建模边连接概率 \(P((v_s, v_i) \in E_c|K)\)，生成新边。
  - 新生成节点数量不超过知识子图节点数的 \(M\%\)（默认为15%）。

- **Evaluation Agent（评价与迭代控制）**
  - 综合初始环境报告 \(R_0\)、当前报告 \(R_t\)、知识子图 \(K_t\) 和合成数据 \(G_t^s\)，进行**语义一致性**与**结构完整性**的双维度质量评估。
  - 计算每个候选节点的质量分，使用自适应阈值 \(\tau_t\) 过滤低质量节点。
  - 收敛判定：结合近期质量梯度与 LLM 目标评估，若未收敛则触发下一轮迭代；否则结束合成。

- **最终图合成**：将原始图与经评估通过的合成节点、边合并，得到扩充后的图 \(G_{new} = G \oplus G_s\)。

### 3. 实验设计

- **数据集与基准**
  - 为模拟数据有限环境，基于 Cora、Citeseer、Wikics、History、Arxiv2023、Children 六个标准文本属性图，创建了采样后的小规模“Sub”变体：SubCora、SubCiteseer、SubWikics、SubHistory、SubArxiv2023、SubChildren。
  - **下游评估架构**：使用 GCN、JKNET、GraphSage、GAT 四种图神经网络。
  - **对比方法**：
    - 不合成：原始数据训练。
    - 经典/LLM 增强：GAugO（经典）、GraphEdit、LLM4RGNN。
    - 经典图合成：GraphSmote、G-Mixup、IntraMix、GraphAdasyn、FG-SMOTE、AGMixup。
    - LLM 图合成：GAG、LLM4NG，以及作者自建的 Mixed-LLM 和 Synthesis-LLM。
  - **评价指标**：Accuracy、F1 Score。

- **额外分析**
  - **图特征分析**：对比合成前后的度分布（KS 检验）、节点聚类系数、标签同质性矩阵。
  - **可解释性评估**：
    - 人工评估：50 名专家对 200 个合成实例进行过程透明度、决策合理性和结果可预测性评分，得出可追溯性分数 \(T_{score}\)。
    - 流形分析：基于 Grassmann 流形计算语义一致性分数。
  - **消融实验**：不同 LLM 基模型（QwQ-32B、Qwen-32B、DeepSeek-R1-32B、LLaMA-33B）、有无 Perception/Evaluation 代理、知识子图大小 \(N\)、新节点比例 \(M\%\)。

### 4. 资源与算力

- **计算平台**：整个实验在 **8 块 80G A100 GPU** 上进行。
- **LLM 基础模型**：默认使用 **QwQ-32B**，通过迭代调用使其扮演不同代理角色；对比实验中也使用了 Qwen-32B、DeepSeek-R1-32B 和 LLaMA-33B。
- **GNN 特征初始化**：使用 Sentence-BERT 生成初始文本嵌入。
- **重复性保障**：每个实验重复 **50 次**，报告均值和标准差。
- **训练时间**：文中未给出具体单次实验的训练时长，但多代理迭代架构必然伴随着较高的 LLM 调用成本。

### 5. 实验数量与充分性

- 实验覆盖 **4 个下游模型 × 6 个数据集**，与 **十余种基线**（含传统、LLM、自建方法）进行了系统对比。
- 额外增加了 **图特征保留分析**（三个结构维度）、**双视角可解释性评估**（人工 + 流形度量）、**多种消融与超参数分析**（LLM 类型、关键组件、子图大小、生成比例）。
- 每个实验多次重复，统计均值与方差，确保了结果的稳定性和客观性；对比基线覆盖多种流派，实验设计公平且全面。

### 6. 论文的主要结论与发现

- **GraphMaster 在所有基准上均显著优于传统与 LLM 基线**，尤其在需要语义丰富的文本属性图合成任务中优势明显（例如，在 Children 数据集上将 GCN 的 F1 从约 33% 提升至 47.8%）。
- **合成图高度保留原始图的结构特征**：多数数据集的度分布 KS 检验无显著差异，聚类系数相似度达 0.835+，标签同质性相似度维持在 0.96 以上。
- **可解释性优异**：人类可追溯性评分达 0.92（远超其他 LLM 基线的 0.66 和 0.59）；流形语义一致性分数高，且与人工评分强相关（r=0.78），表明几何评估方法有效。
- **组件重要性**：移除 Perception Agent 或 Evaluation Agent 导致性能大幅下降（平均 4–5%）；QwQ-32B 在多种 LLM 中表现最佳；知识子图大小 \(N=30\)、新节点比例 \(M=15\%\) 为最优配置。
- 传统图文合成方法在文本属性图上效果普遍较差，甚至可能低于无合成基线，说明语义能力在图合成中至关重要。

### 7. 优点

- **创新性强**：首次提出基于 RAG 视角的多智能体 LLM 框架，系统性地解决文本属性图合成的语义与结构双重需求。
- **架构设计精巧**：四位代理分工明确、迭代协作，分别针对上下文窗口、幻觉控制、结构保持和收敛判断，体现了良好的问题分解。
- **严格的实验与评估体系**：自建数据有限基准、双视角可解释性评估（人工 + Grassmann 流形），并提供了详尽的图特征一致性分析。
- **理论与可复现性**：论文包含信息论与流形学习的理论分析，并承诺开放完整代码和数据，增强了结果的可信度。

### 8. 不足与局限

- **采样偏差风险**：知识子图选取偏向结构中心节点，可能忽略语义重要但拓扑边缘的社区，对度分布严重倾斜或多组件图存在合成盲区。
- **评估依赖 LLM 质量**：评估代理的质量受限于所使用的 LLM 本身，部署时若采用较小模型，评估稳定性可能下降。
- **计算开销大**：多代理迭代过程中包含大量 LLM 调用，对极大规模图的实时合成效率受限，需要复杂的批处理或工程优化。
- **跨域泛化有待验证**：目前仅在学术引文网络及少数特定文本属性图上测试，向其他领域（如生物网络、工业图谱）的迁移能力尚未探明。
- **少数实验细节缺失**：未报告具体单次训练/合成的时间成本，无法精确评估资源消耗。

（完）
