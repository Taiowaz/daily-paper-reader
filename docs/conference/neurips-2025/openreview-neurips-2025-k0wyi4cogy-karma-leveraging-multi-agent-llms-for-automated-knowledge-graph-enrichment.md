---
title: "KARMA: Leveraging Multi-Agent LLMs for Automated Knowledge Graph Enrichment"
title_zh: "KARMA: 利用多代理LLM实现自动化知识图谱丰富"
authors: "Yuxing Lu, Wei Wu, Xukai Zhao, Rui Peng, Jinzhuo Wang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=k0wyi4cOGy"
tags: ["query:graph-llm"]
score: 8.0
evidence: 多代理LLM从文本自动丰富知识图谱
tldr: 手动维护知识图谱难以跟上文献增长速度。本文提出KARMA框架，利用九个协作的LLM代理，从非结构化文本中自动抽取实体、关系并进行模式对齐，实现知识图谱的丰富。在多个生物医学领域数据集上的实验验证了其有效性，为自动化知识工程提供了新方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-k0wyi4cogy/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1164, \"height\": 291, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-k0wyi4cogy/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1447, \"height\": 839, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-k0wyi4cogy/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1177, \"height\": 445, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-k0wyi4cogy/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1389, \"height\": 469, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-k0wyi4cogy/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1391, \"height\": 471, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-k0wyi4cogy/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1389, \"height\": 469, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-k0wyi4cogy/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1465, \"height\": 731, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-k0wyi4cogy/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1453, \"height\": 682, \"label\": \"Table\"}]"
motivation: 知识图谱手动维护难以扩展，需要自动化方法。
method: 设计九个协作的LLM代理，执行实体发现、关系抽取和模式对齐等任务。
result: 在1200篇文献上成功丰富知识图谱，验证了框架有效性。
conclusion: KARMA为大规模知识图谱的自动更新提供了可行路径。
---

## Abstract
Maintaining comprehensive and up-to-date knowledge graphs (KGs) is critical for modern AI systems, but manual curation struggles to scale with the rapid growth of scientific literature. This paper presents KARMA, a novel framework employing multi-agent large language models (LLMs) to automate KG enrichment through structured analysis of unstructured text. Our approach employs nine collaborative agents, spanning entity discovery, relation extraction, schema alignment, and conflict resolution that iteratively parse documents, verify extracted knowledge, and integrate it into existing graph structures while adhering to domain-specific schema. Experiments on 1,200 PubMed articles from three different domains demonstrate the effectiveness of KARMA in knowledge graph enrichment, with the identification of up to 38,230 new entities while achieving 83.1\% LLM-verified correctness and reducing conflict edges by 18.6\% through multi-layer assessments.

---

## 论文详细总结（自动生成）

好的，基于提供的论文内容，以下是为您生成的结构化详细总结。

### 1. 论文的核心问题与整体含义

*   **研究动机与背景**
    *   **知识图谱的维护瓶颈**：知识图谱（KG）对于现代AI系统（如维基数据、DBpedia）至关重要，但科学文献量呈指数级增长（每年超700万篇），传统的人工管理方式已无法满足扩展需求。
    *   **现有方法的局限**：传统NLP方法难以处理特定领域术语和上下文依赖关系，且需要昂贵的监督微调；单一大语言模型（LLM）虽然推理能力强，但存在幻觉、模式不一致和计算成本高等问题，直接应用于知识图谱丰富仍具挑战性。
    *   **核心问题**：如何高效、准确、可扩展地从海量非结构化科学文献中自动提取结构化知识，并将其融入现有知识图谱。

*   **整体含义**
    *   本文提出了一种名为KARMA的***多代理大语言模型框架***，通过九个协作的专用代理，将知识图谱丰富流程分解为实体发现、关系抽取、模式对齐和冲突解决等子任务，旨在实现一个精确、可扩展且模块化的自动化知识图谱更新系统。

### 2. 论文提出的方法论

**核心思想**
KARMA采用分层多代理架构，由一个中央控制器编排九个基于LLM的专门代理，流水线式地完成从文档摄入到知识图谱集成的全过程。其核心创新在于通过多代理协作实现交叉验证，以增强提取知识的可靠性，并通过模块化设计保持灵活性和领域适应性。

**关键技术细节与算法流程**
整个流程被分解为以下几个顺序执行的代理任务（公式用文字说明）：
*   **摄入代理**：检索原始PDF/HTML文档，将其格式标准化，并提取元数据（如作者、日期）。输出标准化文本。
*   **阅读者代理**：将标准化文本分割为摘要、方法等逻辑段落，并根据与当前知识图谱的领域相关性对每个段落打分，过滤掉低分内容。
*   **摘要代理**：将高相关性的文本段落压缩成保留关键实体和关系的简洁摘要，以降噪并提升下游代理的处理效率。
*   **实体提取代理**：从摘要中识别领域相关实体，并将其规范化。它先用LLM进行命名实体识别，再通过词典/本体过滤假阳性，最后通过最小化联合嵌入空间中的距离函数，将实体提及映射到知识图谱中的规范实体。
*   **关系提取代理**：针对规范化后的实体对，利用LLM分类器推断它们之间的关系，形成一个或多个候选三元组（头实体，关系，尾实体）。
*   **模式对齐代理**：检查新提取的实体或关系是否与现有知识图谱的模式（如实体类型、关系类型）匹配。若不匹配，则尝试将其映射到最接近的已有类型，或标记为待审核的新增项。
*   **冲突解决代理**：检测新三元组是否与知识图谱中已有的三元组存在逻辑冲突。通过LLM进行“辩论”来判断是“同意”还是“矛盾”，若为矛盾则丢弃或标记为人工审核。
*   **评估代理**：最终整合多个验证信号，通过加权聚合计算每个三元组的全局置信度、清晰度和相关性分数。只有当这三个分数的均值超过设定阈值时，该三元组才被批准集成到知识图谱中。

### 3. 实验设计

*   **使用数据集**
    *   从PubMed数据库中筛选了三个不同生物医学领域的科学文献作为语料库：
        *   **基因组学语料库**：720篇，聚焦基因变异、调控元件等。
        *   **蛋白质组学语料库**：360篇，涉及蛋白质结构、功能和相互作用网络。
        *   **代谢组学语料库**：120篇，讨论代谢通路、代谢物分析等。
    *   所有文章均为PDF格式。

*   **Benchmark与对比方法**
    *   **单代理基线**: 使用GLM-4模型，在单次生成中直接提取所有三元组的单代理方法。
    *   **不同LLM主干对比**: 为了评估不同LLM作为代理主干的性能，核心组件保持不变。对比了三种模型：
        *   **GLM-4**: 开源9B参数模型。
        *   **GPT-4o**: 闭源多模态模型。
        *   **DeepSeek-v3**: 开源MoE 37B激活参数模型。
    *   **消融实验**: 为了量化各关键代理的贡献，基于DeepSeek-v3骨干模型，分别移除摘要代理、冲突解决代理和评估代理，并与完整版KARMA进行对比。

*   **评估指标**
    在缺乏金标准的情况下，采用了一个多层面的评估框架，包括：
    *   **核心指标**: 平均置信度、平均清晰度、平均相关性。
    *   **图谱统计指标**: 覆盖率增益（新实体数量）、连接性增益（节点度数增量）。
    *   **质量指标**: 冲突率（被冲突解决代理移除的边比例）、LLM评估正确率、问答连贯性得分、人类评估得分。

### 4. 资源与算力

*   论文在“成本分析”部分讨论了计算开销，侧重于令牌使用和处理时间，并给出了不同领域（基因组学、蛋白质组学、代谢组学）的提示令牌、完成令牌和处理时间的分布图。
*   **然而，论文并未明确说明实验所使用的具体硬件资源，如GPU型号、数量或详细的训练/推理时长。**

### 5. 实验数量与充分性

*   **实验数量**: 论文进行了多组、多维度的实验：
    1.  **主实验**: 在三个不同领域的数据集上，分别使用三种LLM骨干模型运行KARMA，构成了一个3x3的实验矩阵，测量了9项指标。
    2.  **消融实验**: 针对性能最优的DeepSeek-v3模型，在三个领域上分别进行了3组消融实验（移除不同代理），构成了9组对比实验。
    3.  **成本分析**: 对不同领域的令牌消耗和处理时间进行了可视化分析。
*   **充分性与公平性**:
    *   **充分性**: 实验设计较为全面，覆盖了不同规模、不同复杂度的领域，并通过多种LLM主干和消融研究来验证框架的鲁棒性和各组件的有效性。评估指标也较为多元，结合了定量统计和定性质量评估。
    *   **客观性与公平性**: 对比基线包括单代理方法，消融实验在同一LLM主干下进行，具有可比性。所有LLM评估均采用独立的DeepSeek-v3模型，以减少自我评估偏差。主要局限在于缺乏基于标准金标准数据集的直接对比，更多依赖于LLM和人工的辅助评估。

### 6. 论文的主要结论与发现

1.  **有效性**: KARMA多代理框架能有效扩展领域知识图谱，其性能显著优于单代理方法（GLM-4主干）。
2.  **性能差异**: 框架在不同领域的表现不同，在文献丰富的领域（如基因组学）能发现最多的新实体。
3.  **LLM主干影响**: LLM主干的选择显著影响知识图谱质量。DeepSeek-v3在整体覆盖率和连接性上表现最佳，GPT-4o在正确率上领先，GLM-4则在特定领域（如代谢组学的清晰度）展现优势。
4.  **多代理关键作用**: 自动的评估和冲突解决机制提升了知识图谱的质量，消融实验证明，移除任何关键代理（特别是摘要、冲突解决和评估代理）都会显著降低最终图谱的正确性、连贯性或一致性。

### 7. 优点

*   **创新的多代理架构**: 将复杂的知识图谱丰富任务分解为九个专用代理的协作，设计清晰、模块化，易于扩展和维护。
*   **多层次的验证机制**: 通过冲突解决代理的逻辑辩论和评估代理的多信号加权评分，有效减少了幻觉和错误知识的引入，提升了最终图谱的可靠性。
*   **系统性的领域适应性评估**: 在基因组学、蛋白质组学三个差异化的生物医学领域进行了测试，展示了框架的泛化能力。
*   **全面的分析与验证**: 不仅提供了整体性能对比，还包含详尽的消融研究和成本分析，并从核心指标、图谱统计和质量指标等多角度进行评估，论证严谨。

### 8. 不足与局限

*   **缺乏金标准评估**: 评估主要依赖LLM和少量人工，而非标准化的生物医学实体与关系基准数据集（如BC5CDR），这可能掩盖系统性错误。尽管设计了多种指标，但与“真实”的偏差程度难以精确量化。
*   **实验领域局限**: 所有实验均在生物医学领域的PubMed文献上进行，其在其他科学领域（如物理、化学）或通用领域的文本上的有效性尚未得到验证。
*   **成本与效率**: 论文虽然分析了令牌消耗，但未明确讨论多代理架构与单代理或传统方法相比的整体时间成本和API调用成本，其大规模应用的经济可行性需进一步评估。
*   **对底层LLM的依赖**: 框架的性能严重依赖于所选LLM主干的能力，可能继承这些模型本身的偏见和局限性。

（完）
