---
title: "Deliberation on Priors: Trustworthy Reasoning of Large Language Models on Knowledge Graphs"
title_zh: 先验审议：基于知识图谱的大语言模型可信推理
authors: "Jie Ma, Ning Qu, Zhitao Gao, Xing Rui, Jun Liu, Hongbin Pei, Jiang Xie, Lingyun Song, Pinghui Wang, Jing Tao, su zhou"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=bulTwq5kNK"
tags: ["query:graph-llm"]
score: 9.0
evidence: 利用知识图谱增强大语言模型推理的忠实性和可靠性
tldr: 针对现有知识图谱检索增强生成未能充分利用知识图谱结构信息的问题，提出了一种逐步知识蒸馏的推理框架，将图谱中的结构化先验和约束融入大语言模型，实验表明该方法能提升推理的忠实性和响应的可靠性，为知识图谱增强的大模型推理提供了新思路。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-bultwq5knk/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1290, \"height\": 649, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-bultwq5knk/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 496, \"height\": 399, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-bultwq5knk/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1440, \"height\": 772, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-bultwq5knk/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 877, \"height\": 306, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-bultwq5knk/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1455, \"height\": 388, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-bultwq5knk/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1459, \"height\": 838, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-bultwq5knk/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1448, \"height\": 1135, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-bultwq5knk/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 914, \"height\": 429, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-bultwq5knk/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1447, \"height\": 729, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-bultwq5knk/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 726, \"height\": 391, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-bultwq5knk/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 510, \"height\": 230, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-bultwq5knk/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 681, \"height\": 267, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-bultwq5knk/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 727, \"height\": 343, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-bultwq5knk/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1388, \"height\": 223, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-bultwq5knk/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1442, \"height\": 302, \"label\": \"Table\"}]"
motivation: 现有方法未充分利用知识图谱中的结构信息和约束，导致大模型推理的忠实性和可靠性不足。
method: 提出逐步知识蒸馏策略，将图谱结构信息和显式/隐式约束整合进LLM推理过程。
result: 实验证明该方法能提升LLM在知识图谱相关任务上的忠实性和可靠性。
conclusion: 通过充分利用KG先验，有效缓解了LLM幻觉，实现了更可信的推理。
---

## Abstract
Knowledge graph-based retrieval-augmented generation seeks to mitigate hallucinations in Large Language Models (LLMs) caused by insufficient or outdated knowledge. However, existing methods often fail to fully exploit the prior knowledge embedded in knowledge graphs (KGs), particularly their structural information and explicit or implicit constraints. The former can enhance the faithfulness of LLMs' reasoning, while the latter can improve the reliability of response generations. Motivated by these, we propose a trustworthy reasoning framework, termed Deliberation over Priors (\texttt{DP}), which sufficiently utilizes the priors contained in KGs. Specifically, \texttt{DP} adopts a progressive knowledge distillation strategy that integrates structural priors into LLMs through a combination of supervised fine-tuning and Kahneman-Tversky Optimization, thereby improving the faithfulness of relation path generation. Furthermore, our framework employs a reasoning-introspection strategy, which guides LLMs to perform refined reasoning verification based on extracted constraint priors, ensuring the reliability of response generation. Extensive experiments on three benchmark datasets demonstrate that \texttt{DP} achieves new state-of-the-art performance, especially a H@1 improvement of 13% on the ComplexWebQuestions dataset, and generates highly trustworthy responses. We also conduct various analyses to verify its flexibility and practicality. Code is available at [https://github.com/mira-ai-lab/Deliberation-on-Priors](https://github.com/mira-ai-lab/Deliberation-on-Priors).

---

## 论文详细总结（自动生成）

好的，这是对论文《Deliberation on Priors: Trustworthy Reasoning of Large Language Models on Knowledge Graphs》的结构化、深入、客观总结。

### 1. 论文的核心问题与整体含义

-   **核心问题**：当前基于知识图谱的检索增强生成方法，虽然能缓解大语言模型的幻觉问题，但普遍未能充分利用知识图谱中蕴含的**先验知识**。
-   **两大未被充分利用的先验**：
    1.  **结构信息**：即连接主题实体与答案的关系路径。现有方法对其利用不足，导致推理的**忠实性** 不高。
    2.  **显式与隐式约束**：如类型约束、多实体约束、时间约束等。忽视这些约束会影响生成答案的**可靠性**。
-   **整体含义**：论文旨在通过一个名为 **Deliberation over Priors (DP)** 的框架，引导大语言模型在推理时充分“审议”并利用知识图谱的这两类先验知识，从而生成更忠实、可靠的答案。

### 2. 论文提出的方法论

DP 框架由一个离线阶段和一个在线阶段构成，包含四个核心模块：**Distillation (蒸馏)**、**Planning (规划)**、**Instantiation (实例化)** 和 **Introspection (内省)**。

#### 离线阶段：知识蒸馏

-   **核心思想**：通过渐进式知识蒸馏策略，将知识图谱的结构先验（关系路径）注入大语言模型。
-   **关键技术细节**：
    1.  **弱监督信号收集**：在训练集上，利用 Dijkstra 算法从主题实体到答案实体，找到所有最短关系路径，形成“问题-路径”对的多对一映射，作为弱监督信号。
    2.  **监督微调**：利用上述弱监督信号，对大语言模型进行微调，使其学会根据问题和主题实体生成忠实的关系路径。其优化目标是最大化生成正确路径序列的条件对数似然。
    3.  **Kahneman-Tversky 优化**：为进一步提升生成路径的质量，构建偏好数据集，包含正样本（正确路径）和通过截断、交换、删除等方式生成的负样本。由于正负样本比例极不平衡，采用对数据不平衡更鲁棒的 KTO 算法进行偏好优化，使模型倾向于生成语义连贯、结构忠实的路径。

#### 在线阶段：规划、实例化与内省

-   **核心思想**：利用蒸馏后的大语言模型进行路径规划，再通过基于约束先验的内省机制确保推理的可靠性。
-   **算法流程**：
    1.  **Planning (规划)**：给定问题和主题实体，蒸馏后的大语言模型生成一个多样化的候选关系路径集合。
    2.  **Instance Selection & Instantiation (路径选择与实例化)**：
        -   大语言模型根据路径与问题的语义相关性，从候选集合中选择一条最佳关系路径。
        -   在知识图谱中遍历该关系路径，从主题实体开始检索具体实体，得到一条完整的实例化推理路径。
    3.  **Introspection (内省)**：
        -   **约束提取**：大语言模型从问题中提取预定义的约束（如类型、多实体约束等）。
        -   **约束验证**：大语言模型被要求验证当前实例化推理路径是否满足所有提取出的约束。
        -   如果满足，则基于该路径生成最终答案。
        -   **如果不满足，则触发“回溯”机制**：将违反约束的反馈信息返回给路径选择模块，要求大语言模型从剩余候选路径中重新选择，并再次进行实例化和内省，直到找到满足约束的路径或候选路径耗尽。

### 3. 实验设计

-   **数据集**：在三个多跳知识图谱问答基准数据集上进行评估：
    -   **WebQuestionsSP (WebQSP)**：最多2跳推理。
    -   **ComplexWebQuestions (CWQ)**：最多4跳推理。
    -   **MetaQA**：包含1跳、2跳、3跳问题。
-   **评估指标**：采用 Hit (H)、Hits@1 (H@1) 和 F1 分数。
-   **对比方法**：与三大类、共十余种前沿方法进行了全面比较：
    -   **监督学习方法**：EmbedKGQA, TransferNet, UniKGQA, RoG, AMAR, GNN-RAG。
    -   **上下文学习方法**：ToG, PoG, Readi, DoG。
    -   **混合学习方法**：Interactive-KBQA, LightPROF。
    -   同时将**直接提问的 LLM（如 GPT-4）** 作为基础基准。

### 4. 资源与算力

-   **硬件配置**：所有训练在**2块 NVIDIA A800-80GB GPU** 上进行。
-   **训练设置**：
    -   对 LLaMA3.1-8B-Instruct 基础模型使用 LoRA 进行高效微调。
    -   监督微调 2 个 epoch，KTO 优化训练 1 个 epoch。
    -   SFT 和 KTO 的批次大小均为 4。

### 5. 实验数量与充分性

实验设计相当充分和深入，包含以下组别：

-   **主实验**：在三个数据集上与超过 10 种基线方法进行全方位性能比较。
-   **灵活性验证实验**：将 DP 框架与 **6 种不同的大语言模型** 集成，验证其泛化能力。
-   **消融实验**：系统地移除了框架中的**所有关键组件**（KTO优化、数据扰动、内省模块、回溯反馈、人工预定义约束），以验证各部分的贡献。
-   **影响分析实验**：
    -   分析了先验知识对**路径生成和约束提取**精度的影响。
    -   对**错误案例**进行归类分析。
    -   分析了**回溯机制**在不同模型上的触发频率。
-   **效率分析实验**：从**调用大语言模型次数、输入/输出/总 Token 消耗**等方面，与多个基线方法进行效率比较。
-   **额外分析**：探讨了不同数量的少样本示例对性能的影响。

这些实验覆盖了性能、泛化性、内部机制、效率和适用性等多个维度，对比公正，消融彻底，能够充分支撑论文的结论。

### 6. 论文的主要结论与发现

-   **性能顶尖**：DP 框架在三个基准数据集上均取得了新的最先进性能，特别是在 CWQ 数据集上，H@1 指标相比最强基线（LightPROF）**提升了 16.5%**，且结果方差小，非常稳定。
-   **更具可信度**：DP 显著缩小了 Hit 与 F1 之间的巨大差距，证明其生成的答案不仅包含正确结果，而且排名更靠前、精确率更高，展现了更强的可靠性和鲁棒性。
-   **先验至关重要**：充分利用结构信息（通过蒸馏）和约束先验（通过内省和回溯）是取得高可靠性的关键。任何组件的移除都会导致性能下降，尤其是移除“内省”模块导致性能下降最明显。
-   **灵活且高效**：DP 可有效集成多种不同的大语言模型，且在达到顶尖性能的同时，调用大语言模型的次数和消耗的总 Token 数远低于部分主流方法，展现了优秀的实用性。

### 7. 优点

-   **问题洞察深刻**：准确识别了现有方法的痛点，即对知识图谱“结构”和“约束”两种隐式先验知识的利用不足。
-   **方法设计精巧**：创新性地将“审议”思想引入推理过程，形成“规划-实例化-内省-回溯”的闭环，逻辑清晰。特别是引入 KTO 来处理不平衡的路径偏好数据，很有针对性。
-   **实验极其扎实全面**：不仅在主流数据集上与大量基线对比，还进行了多维度、多基础的消融和分析，论证力度强。
-   **实用价值高**：框架表现出良好的模型兼容性和较低的 API 调用成本，证明了其在实际应用中的潜力。

### 8. 不足与局限

-   **约束依赖人工**：预定义的约束类型是目前方法的一个核心局限。在应用到新的垂直领域时，需要人类专家介入来定义新的约束类型。论文虽尝试了自动总结，但效果不佳，这是未来需要突破的关键点。
-   **路径依赖性强**：错误案例分析表明，路径生成仍是主要的误差来源之一。如果第一步生成的候选路径质量不高，后续的内省和回溯机制也难以修正，说明对生成模型的依赖依然很强。
-   **推理能力受限**：即使选对了路径，大语言模型仍可能因过度依赖自身内部知识或遵循指令能力不足而产生推理错误或格式错误。
-   **资源消耗**：离线阶段需要为每个数据集单独训练一个路径生成器，虽然训练效率较高，但与完全免训练的方法相比，还是增加了一定的准备成本。

（完）
