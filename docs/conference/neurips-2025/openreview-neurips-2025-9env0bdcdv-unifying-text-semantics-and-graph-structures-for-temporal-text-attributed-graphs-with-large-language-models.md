---
title: Unifying Text Semantics and Graph Structures for Temporal Text-attributed Graphs with Large Language Models
title_zh: 使用大语言模型统一时序文本属性图中的文本语义与图结构
authors: "Siwei Zhang, Yun Xiong, Yateng Tang, Jiarong Xu, Xi Chen, Zehao Gu, Xuehao Zheng, Zi'an Jia, Jiawei Zhang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=9env0BdcDV"
tags: ["query:graph-llm"]
score: 10.0
evidence: 提出CROSS框架，用大语言模型扩展时序图神经网络，实现文本语义与图结构的协同建模
tldr: 针对时序文本属性图中动态文本语义与演变图结构难以协同建模的问题，提出CROSS框架，将大语言模型无缝接入现有时序图神经网络，联合学习时序文本和图拓扑，实验表明其在多种任务上优于传统方法，为图文合一学习提供了新方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-9env0bdcdv/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1402, \"height\": 539, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9env0bdcdv/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1433, \"height\": 300, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9env0bdcdv/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1439, \"height\": 517, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9env0bdcdv/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1409, \"height\": 307, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9env0bdcdv/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 716, \"height\": 301, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9env0bdcdv/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 699, \"height\": 259, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9env0bdcdv/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 783, \"height\": 280, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9env0bdcdv/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 719, \"height\": 265, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9env0bdcdv/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 672, \"height\": 284, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9env0bdcdv/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1438, \"height\": 1051, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9env0bdcdv/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 669, \"height\": 284, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9env0bdcdv/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1422, \"height\": 312, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9env0bdcdv/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1337, \"height\": 363, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9env0bdcdv/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1409, \"height\": 348, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9env0bdcdv/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 778, \"height\": 277, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9env0bdcdv/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 630, \"height\": 237, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9env0bdcdv/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 637, \"height\": 189, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9env0bdcdv/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 646, \"height\": 243, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9env0bdcdv/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 625, \"height\": 179, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9env0bdcdv/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 643, \"height\": 272, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-9env0bdcdv/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 839, \"height\": 236, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9env0bdcdv/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1465, \"height\": 659, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9env0bdcdv/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1439, \"height\": 463, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9env0bdcdv/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1378, \"height\": 445, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9env0bdcdv/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1464, \"height\": 274, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9env0bdcdv/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1433, \"height\": 654, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9env0bdcdv/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1458, \"height\": 594, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9env0bdcdv/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1467, \"height\": 593, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9env0bdcdv/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1455, \"height\": 299, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9env0bdcdv/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 838, \"height\": 303, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9env0bdcdv/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1451, \"height\": 241, \"label\": \"Table\"}]"
motivation: 现有TGNN忽略文本的时序演变和语义-结构协同，导致表示学习受限。
method: 提出灵活框架CROSS，将LLM嵌入与TGNN结合，实现语义和结构的协同训练。
result: 在多个时序图任务上取得显著性能提升，验证了联合建模的优势。
conclusion: 通过融合LLM，有效捕捉了动态文本语义与图结构，提升了时序图学习。
---

## Abstract
Temporal graph neural networks (TGNNs) have shown remarkable performance in temporal graph modeling. However, real-world temporal graphs often possess rich textual information, giving rise to temporal text-attributed graphs (TTAGs). Such combination of dynamic text semantics and evolving graph structures introduces heightened complexity. Existing TGNNs embed texts statically and rely heavily on encoding mechanisms that biasedly prioritize structural information, overlooking the temporal evolution of text semantics and the essential interplay between semantics and structures for synergistic reinforcement.
To tackle these issues, we present $\textbf{CROSS}$, a flexible framework that seamlessly extends existing TGNNs for TTAG modeling. CROSS is designed by decomposing the TTAG modeling process into two phases: (i) temporal semantics extraction; and (ii) semantic-structural information unification. The key idea is to advance the large language models (LLMs) to $\textit{dynamically}$ extract the temporal semantics in text space and then generate $\textit{cohesive}$ representations unifying both semantics and structures.
Specifically, we propose a Temporal Semantics Extractor in the CROSS framework, which empowers LLMs to offer the temporal semantic understanding of node's evolving contexts of textual neighborhoods, facilitating semantic dynamics.
Subsequently, we introduce the Semantic-structural Co-encoder, which collaborates with the above Extractor for synthesizing illuminating representations by jointly considering both semantic and structural information while encouraging their mutual reinforcement. Extensive experiments show that CROSS achieves state-of-the-art results on four public datasets and one industrial dataset, with 24.7\% absolute MRR gain on average in temporal link prediction and 3.7\% AUC gain in node classification of industrial application.

---

## 论文详细总结（自动生成）

好的，我将基于提供的论文内容，生成详细的中文总结。

### 1. 论文的核心问题与整体含义

*   **研究背景**：现实世界中的时序图（如电商交易网络）不仅包含随时间演变的图结构（用户交互记录），节点和边还附带丰富的文本信息（如用户简介、商品评论），这类图被称为时序文本属性图（TTAGs）。
*   **核心问题**：现有时序图神经网络（TGNNs）在处理TTAGs时存在两个根本性局限：
    1.  **忽略文本语义的动态性**：它们通常使用预训练语言模型（如MiniLM）静态地嵌入文本，无法捕捉节点周边文本语境随时间发生的动态变化（例如，“apple”一词根据用户兴趣变迁，可能从“水果”语义转向“智能手机”语义）。
    2.  **对语义-结构相互增强的编码能力不足**：TGNNs严重偏向于利用图拓扑结构信息，缺乏一种有效的机制来融合并促进文本语义与图结构之间的协同增强，导致生成的表示次优且易受结构噪声影响。
*   **整体含义**：本文旨在解决TTAG建模这一尚未被充分探索的问题，提出一个框架来同时处理动态文本语义和演变图结构，并实现二者的深度融合与相互强化。

### 2. 论文提出的方法论

论文提出了**CROSS**框架，它通过与大语言模型（LLMs）结合，无缝扩展现有的TGNNs。其核心思想是将TTAG建模分解为两个阶段：时序语义提取和语义-结构信息统一。

*   **核心思想**：提升LLMs的能力，使其能**动态地**提取文本语义的动态性，并生成**统一的、内聚的**表示，将语义与结构信息融为一体。

*   **关键技术细节与流程**：
    1.  **时序语义提取器 (Temporal Semantics Extractor)**：
        *   **目的**：解决现成LLM静态推理的局限，赋予其动态推理能力，以捕捉节点语境的语义演变。
        *   **实现方式**：引入**时序推理链**。为避免在每个时间戳都调用LLM带来的高昂成本，提取器会以等交互间隔为每个节点采样 `m` 个推理时间点。
        *   **流程**：对于节点 `u` 在推理时间点 `t`，提取器会检索其历史交互记录，并构造提示（Prompt），引导LLM动态总结该节点此时的文本化邻域信息，生成关于节点语境的语义摘要。通过在不同时间点进行这种多轮调用，即可获得一系列反映了语义演变的文本摘要。

    2.  **语义-结构协同编码器 (Semantic-structural Co-encoder)**：
        *   **目的**：解决现有编码器偏向结构、无法实现语义-结构深度结合的问题。
        *   **架构**：这是一个多层的、迭代式的架构，每一层包含三个组件，实现了两种模态（语义和结构）在编码过程中的深度融合。
            *   **语义层**：使用Transformer编码器处理由LLM生成的、带有时序信息的语义摘要特征，生成语义表示。
            *   **结构层**：灵活地使用任意现成TGNN的编码块（如TGAT, TGN, DyGFormer），通过时序注意力机制聚合邻居信息，生成结构表示。
            *   **跨模态混合器**：这是实现深度融合的关键。它将当前层最新的语义表示和结构表示进行拼接，并通过一个MLP进行混合，然后将混合后的特征再拆分回语义和结构表示流，供下一层继续处理，实现双向的信息传递与增强。
        *   **最终表示**：模型的最终输出由多层的语义、结构及混合表示共同拼接，再通过一个MLP层映射得到。

*   **训练**：采用时序链路预测任务作为训练信号，使用交叉熵损失函数。

### 3. 实验设计

*   **数据集**：使用了五个数据集，覆盖不同领域和规模：
    *   四个**公开数据集**：Enron（邮件）、GDELT（政治事件）、ICEWS1819（政治事件）、Googlemap\_CT（谷歌地图评论）。
    *   一个**工业数据集**：来自微信支付的脱敏电商交易数据，规模达百万级节点。
*   **基准对比方法**：选择了11个先进的现有方法作为基线进行对比，包括JODIE, DyRep, TGAT, TGN, CAWN, PINT, TCL, GraphMixer, DyGFormer, LKD4DyTAG, FreeDyG。此外，还评估了DeepSeek-v2大模型的零样本和一镜头性能。
*   **下游任务**：
    *   **时序链路预测**：包括直推式和归纳式两种设置。
    *   **节点分类**：在工业数据集中进行金融风控反欺诈应用。
*   **模型变体**：CROSS作为一个灵活框架，在实验中被用于增强三种代表性的TGNN骨架模型：TGAT, TGN, DyGFormer（在结果表格中表示为模型名+）。

### 4. 资源与算力

*   论文明确提到：所有训练均在一台配备**72核CPU、128GB内存和四块Nvidia Tesla V100 GPU**的服务器上进行。
*   关于LLM调用，论文提供了详细的成本统计，默认LLM（DeepSeek-v2）在所有五个数据集上的总花费为 **200.34美元**。

### 5. 实验数量与充分性

实验设计**非常充分、客观且公平**，具体体现在：
*   **多数据集评估**：在**四个公开和一个工业共五个数据集**上进行测试，覆盖了不同规模和领域。
*   **多任务评估**：进行了**链路预测**（直推式与归纳式）和**节点分类**两项任务，验证了模型在不同下游任务中的泛化能力。
*   **与众多基线对比**：与**11个先进的TGNN模型及LLM基线**进行了全面比较，结果稳固。
*   **详尽的消融研究**：
    *   **模型组件消融**：分别移除时序语义提取器、语义-结构协同编码器、跨模态混合器、时序推理链等关键部件，验证了各组件的有效性。
    *   **文本来源与编码策略消融**：对比了原始文本与LLM生成文本，以及在语义编码、结构编码、协同编码三种策略下的性能，证明了LLM生成文本的价值和协同编码机制的优越性。
    *   **LLM选择消融**：测试了DeepSeek-v2, GPT-4o, Llama3-8b, Vicuna-7b, Mistral-7b等多种LLM作为骨干的效果。
*   **鲁棒性研究**：
    *   **结构噪声鲁棒性**：通过按不同比例随机替换邻居节点引入噪声，验证了模型对结构噪声的强鲁棒性。
    *   **编码层数鲁棒性**：测试了不同编码层数（1至5层）下的性能，显示模型性能随层数加深持续提升。
*   **参数研究**：探讨了关键超参数（最大推理次数 `m`）对性能的影响。
*   **可扩展性澄清**：详细说明了LLM调用的成本、耗时及提高效率的策略。
*   **案例研究**：定性分析了模型如何学习注意力权重和表示分布，直观展示了模型的有效性。

### 6. 论文的主要结论与发现

*   **性能显著提升**：CROSS框架在多个数据集和任务上均取得了**最优性能**。在时序链路预测任务中，MRR平均绝对提升达 **24.7%**；在工业应用的节点分类任务中，AUC提升 **3.7%**。
*   **骨架模型无关性**：CROSS能显著提升不同TGNN骨架的性能，验证了其作为灵活框架的有效性。
*   **语义与结构互补并相互增强**：实验证明，LLM提供的语义信息是结构信息的有效补充，通过协同编码机制可以实现二者的深度融合，尤其是在结构噪声高时，语义信息能提供强大的鲁棒性。

### 7. 优点

*   **问题新颖**：率先系统性地解决TTAGs中语义动态性和语义-结构协同两大难题。
*   **方法创新**：设计了**时序推理链**和**语义-结构协同编码器**两个巧妙组件，前者优雅地让LLM具备了动态时序推理能力，后者则创新性地在编码过程中完成了多模态的深度融合。
*   **框架灵活**：CROSS设计为与现有TGNNs兼容的无缝扩展，具有很高的实用价值和通用性。
*   **理论支撑**：提供了理论分析，证明统一语义与结构能比仅依赖结构获得更具表达力的信息。
*   **实验严谨扎实**：实验设计全面系统，在五个数据集、多个任务、多种配置下进行了详尽的对比、消融和鲁棒性分析，结论极具说服力。

### 8. 不足与局限

*   **LLM语义提取器依赖1跳邻域**：论文指出，时序语义提取器目前只利用了节点的1跳历史交互。对于高阶拓扑语义至关重要的场景，这可能是一个限制。
*   **LLM调用成本**：尽管提出了改进效率的策略并论证了可扩展性，但引入LLM仍然带来了额外的计算和经济成本，这可能在某些对推理延迟或成本极度敏感的应用中构成挑战。
*   **工业数据集细节有限**：出于商业保密，论文对工业数据的描述（如具体字段、文本长度等）不够详尽，这可能影响在类似工业场景中复现其效果的可操作性。
*   **编码机制与LLM文本的适配性**：消融实验中发现LLM生成的文本并非在所有编码机制下都表现更好（如在纯结构编码中提升有限），这说明需要更深入探索如何最大化利用LLM文本的潜力。

（完）
