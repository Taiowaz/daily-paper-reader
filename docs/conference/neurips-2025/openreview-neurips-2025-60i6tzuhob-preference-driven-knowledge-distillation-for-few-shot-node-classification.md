---
title: Preference-driven Knowledge Distillation for Few-shot Node Classification
title_zh: 偏好驱动的知识蒸馏用于少样本节点分类
authors: "Xing Wei, Chunchun Chen, Rui Fan, Xiaofeng Cao, Sourav Medya, Wei Ye"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=60I6TzuHOb"
tags: ["query:graph-llm"]
score: 10.0
evidence: 提出偏好驱动的知识蒸馏框架，协同大语言模型与图神经网络用于文本属性图少样本节点分类
tldr: 针对文本属性图上GNN依赖标注且单机制难以处理多样局部拓扑，LLM可扩展性差的问题，提出偏好驱动知识蒸馏框架PKD，利用LLM的预测蒸馏到GNN教师，并通过GNN偏好选择器提升蒸馏质量，在多个基准上大幅提升少样本节点分类性能，展现了图与大模型协同的潜力。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-60i6tzuhob/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1436, \"height\": 790, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-60i6tzuhob/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 584, \"height\": 371, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-60i6tzuhob/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 596, \"height\": 503, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-60i6tzuhob/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 700, \"height\": 476, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-60i6tzuhob/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 701, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-60i6tzuhob/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1458, \"height\": 1200, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-60i6tzuhob/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1456, \"height\": 747, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-60i6tzuhob/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1454, \"height\": 280, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-60i6tzuhob/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1163, \"height\": 444, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-60i6tzuhob/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1448, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-60i6tzuhob/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1438, \"height\": 162, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-60i6tzuhob/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1438, \"height\": 193, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-60i6tzuhob/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 526, \"height\": 302, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-60i6tzuhob/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1446, \"height\": 256, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-60i6tzuhob/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1476, \"height\": 1393, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-60i6tzuhob/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1471, \"height\": 1398, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-60i6tzuhob/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1465, \"height\": 1491, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-60i6tzuhob/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 678, \"height\": 133, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-60i6tzuhob/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1137, \"height\": 165, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-60i6tzuhob/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1427, \"height\": 123, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-60i6tzuhob/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 816, \"height\": 167, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-60i6tzuhob/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 723, \"height\": 229, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-60i6tzuhob/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1010, \"height\": 158, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-60i6tzuhob/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 655, \"height\": 172, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-60i6tzuhob/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 863, \"height\": 178, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-60i6tzuhob/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 723, \"height\": 168, \"label\": \"Table\"}]"
motivation: GNN依赖人工标注，且单一机制难以处理TAG的复杂局部拓扑；LLM可零/少样本学习但扩展性差。
method: 提出PKD框架，通过GNN偏好驱动的节点选择，将LLM预测蒸馏到GNN教师，再蒸馏到学生。
result: 在多个TAG数据集上，少样本分类准确率显著超越单独GNN或LLM方法。
conclusion: 通过偏好蒸馏有效结合LLM与GNN优势，为图表示学习提供了新方案。
---

## Abstract
Graph neural networks (GNNs) can efficiently process text-attributed graphs (TAGs) due to their message-passing mechanisms, but their training heavily relies on the human-annotated labels. Moreover, the complex and diverse local topologies of nodes of real-world TAGs make it challenging for a single mechanism to handle. Large language models (LLMs) perform well in zero-/few-shot learning on TAGs but suffer from a scalability challenge. Therefore, we propose a preference-driven knowledge distillation (PKD) framework to synergize the complementary strengths of LLMs and various GNNs for few-shot node classification. Specifically, we develop a GNN-preference-driven node selector that effectively promotes prediction distillation from LLMs to teacher GNNs. To further tackle nodes' intricate local topologies, we develop a node-preference-driven GNN selector that identifies the most suitable teacher GNN for each node, thereby facilitating tailored knowledge distillation from teacher GNNs to the student GNN. Extensive experiments validate the efficacy of our proposed framework in few-shot node classification on real-world TAGs.
Our code can be available at <https://github.com/GEEX-Weixing/PKD>.

---

## 论文详细总结（自动生成）

# 论文结构化总结：Preference-driven Knowledge Distillation for Few-shot Node Classification

## 1. 论文的核心问题与整体含义
*   **研究动机**：文本属性图上的节点分类面临两大瓶颈。
    *   **标签稀缺性**：图神经网络的训练高度依赖大量人工标注的节点标签，而人工标注成本高昂。
    *   **拓扑复杂性**：真实世界图中节点的局部拓扑结构复杂多样，单一的图神经网络消息传递机制难以有效处理所有节点。
    *   **大模型局限**：大语言模型虽然具备强大的零样本/少样本学习能力，但存在推理效率低、扩展性差的问题。
*   **核心问题**：如何在极少量真实标签的情况下，有效协同大语言模型和图神经网络各自的优势，以提升文本属性图上的节点分类性能。

## 2. 论文提出的方法论
论文提出了一个名为**偏好驱动知识蒸馏**的框架，其核心思想是通过两个关键模块，实现从大语言模型到“图神经网络教师模型”，再到“图神经网络学生模型”的两阶段知识蒸馏，并为每个节点定制最合适的知识来源。

*   **核心思想**：利用大语言模型的标注能力来增强图神经网络教师，同时根据不同节点的局部拓扑特性，动态选择最合适的教师模型来进行知识迁移，从而训练出性能更强的学生模型。
*   **关键技术细节**：
    *   **大语言模型微调**：为了让大语言模型能理解图拓扑，论文设计了**图拓扑感知（GTA）提示**进行微调。该提示包含连接性判断、节点度查询、环路检测和文本生成四种任务，旨在增强大语言模型对图结构的推理能力。
    *   **图神经网络偏好的节点选择器**：该模块用于选择哪些节点的标签需要由大语言模型来标注，以最大程度地增强教师模型。
        *   **核心指标（K-不确定性）**：基于多个教师模型之间预测分布的KL散度来衡量节点的不确定性。节点的K不确定性越高，说明模型对其的认知分歧越大。
        *   **选择策略**：优先选择K不确定性高的节点，将其交由微调后的大语言模型进行标注。同时，设计了一个基于距离的邻居选择器模块，用于在提示中加入节点的结构和邻居信息，帮助大语言模型生成更高质量的伪标签。
    *   **节点偏好的图神经网络选择器**：该模块为每个节点动态选择最适合的教师模型，以实现定制化的知识蒸馏。
        *   **形式化方法**：将教师选择问题建模为一个**强化学习**任务。将微调后的大语言模型作为智能体，节点的语义、结构和预测属性作为状态，选择的教师模型作为动作，学生模型的性能表现作为奖励。
        *   **优化算法**：使用**近端策略优化（PPO）**算法来训练该选择器，使其能够根据节点属性，做出最优的教师分配决策。
*   **最终目标函数**：学生模型的最终训练损失由三部分加权组合而成，包括与所选教师模型之间的蒸馏损失、与真实标签之间的交叉熵损失，以及使预测更尖锐的熵正则化损失。

## 3. 实验设计
*   **数据集**：在9个真实世界的文本属性图上进行了评估，这些图具有不同的同配比，具体包括：
    *   **高异配性图**：`Cornell`、`Washington`、`Texas`、`Wisconsin`
    *   **中/高同配性图**：`Amazon Ratings`、`Ogbn-Arxiv`、`Wiki CS`、`PubMed`、`Cora`
*   **任务场景与基准设置**：
    *   **少样本场景**：从数据集中仅随机选取每类1、3或5个节点作为真实标签进行模型训练。
    *   **对比方法**：将PKD与四类主流方法进行了全面比较。
        *   **先进图神经网络**：GCNII， EGNN
        *   **大模型增强的方法**：LLMGNN， GAugLLM
        *   **图自训练方法**：Self-training, AGST， IceBerg
        *   **多教师知识蒸馏方法**：KDGA, MSKD, BGNN, MTAAM, FairGKD
    *   **伪标签有效性验证**：设计实验对比了在同样数量下，使用LLM生成的伪标签和真实标签对下游模型（GCNII、IceBerg）性能的影响。
    *   **文心一言/模型通用性验证**：将骨干文心一言从`Llama-3.1-8B-Instruct`替换为`Qwen2.5-7B-Instruct`和`Mixtral-7B-Instruct-v0.3`进行测试。

## 4. 资源与算力
*   **硬件**：在NVIDIA A800-SXM4-80GB GPU和Intel(R) Xeon(R) CPU Max 9468上进行所有实验。
*   **软件**：实验基于PyTorch、PyG、Transformers和vllm等框架构建。
*   **训练时间**：文中在附录中给出了详细的运行时间分析。
    *   **大语言模型微调**：使用LoRA策略在`Llama-3.1-8B-Instruct`上进行微调，耗时约9小时41分钟。
    *   **推理与训练**：在`Cora`数据集上，大语言模型标注耗时0.11 GPU小时，重新训练教师图神经网络耗时约2.5秒，节点偏好选择器单轮耗时7.9秒，峰值显存454.62 MB。整个PKD框架的单轮训练时间为7.314秒。该方案由于引入了大语言模型，训练时间与系统资源开销明显高于传统图神经网络。

## 5. 实验数量与充分性
论文设计了非常全面且充分的实验，具体包括：
*   **1项主要性能对比实验**：在9个数据集上，使用3种不同的少样本设置（# LN 1, 3, 5），对比了PKD与4大类共12种基线方法的性能。
*   **1项模型通用性实验**：在8个数据集上替换了2种不同的大语言模型骨干进行验证。
*   **1项消融研究**：系统性地检验了图拓扑感知提示、基于距离的邻居选择器和节点偏好排序表三个核心组件对性能的提升作用，以及不含强化学习的教师选择策略的效果。
*   **1项奖励函数消融**：分析了奖励函数中不同组成部分（准确率、交叉熵损失、蒸馏损失）的贡献。
*   **1项伪标签质量验证实验**：对比了LLM生成的伪标签与真实标签对下游模型性能的影响。
*   **3项超参数敏感性分析**：探究了邻居数K、节点标注比率、损失函数权重 (α, β, γ, η) 对性能的影响。
*   **1项模型规模影响分析**：测试了不同参数量级别的大语言模型（7B/14B/32B）对PKD性能的影响。
*   **1项时间效率分析**：在`Cora`数据集上对比了所有方法的单轮训练时间，体现了精度与效率间的权衡。

这些实验设计覆盖了多个数据集、多种骨干模型、多个关键模块和超参数，对比基线选择有代表性，分析维度全面，充分且客观地支撑了论文的核心论点。

## 6. 论文的主要结论与发现
*   **PKD框架在少样本节点分类任务上表现显著优越**。在仅使用1、3或5个真实标签的情况下，PKD在所有9个数据集上的性能均大幅度超越所有基线方法，甚至超越了部分使用更多真实标签的方法。
*   **图拓扑感知提示微调能有效赋能大语言模型**，使其具备理解图结构的能力，从而生成高质量的伪标签，这是性能提升的关键。
*   **双偏好驱动的设计至关重要**。“图神经网络偏好的节点选择器”通过识别高不确定性节点提升了蒸馏效率；“节点偏好的图神经网络选择器”通过为每个节点定制教师，解决了单一消息传递机制无法处理复杂拓扑的难题。
*   **模型具有较好的通用性**，替换不同的大语言模型骨干后，PKD仍能保持优秀的性能表现。

## 7. 优点
*   **创新性问题建模与解决思路**：首次提出“偏好驱动”的知识蒸馏视角，巧妙地用两个互补的选择器（基于图神经网络的节点选择和基于节点的图神经网络选择），同时解决大语言模型的扩展性问题和图神经网络处理复杂拓扑的局限性。
*   **方法设计的深度与精细度**：框架设计非常精巧，从“使大语言模型懂图”的微调，到“选择哪些节点让大语言模型标注”的不确定性度量，再到“为每个节点选老师”的强化学习设计，环环相扣，形成了一个端到端的协同学习框架。
*   **实验设计极其扎实充分**：在9个不同特性的数据集上进行了全面验证，对比方法覆盖了多个主流流派，并且设计了详尽的消融实验、超参数分析和模型通用性实验，结论极具说服力。此外，对计算资源和时间的分析也体现了严谨性。

## 8. 不足与局限
*   **应用场景的局限性**：该方法明确设计用于文本属性图，其核心组件（如利用文本信息构造提示）使其难以直接迁移到非文本属性的通用图结构数据上。
*   **计算效率与成本的挑战**：尽管解决了大语言模型的扩展性问题，但框架本身的训练仍涉及大语言模型微调、推理和强化学习训练环节，训练时间和计算资源需求远高于传统图神经网络。论文在效率部分也承认了精度与时间成本之间的权衡。
*   **公平性考量缺失**：虽然论文有“Broader Impact”章节，提及了公平性，但在整个方法和实验设计中，并未探讨或衡量模型在不同节点群体（如不同度数的节点、不同类别）上是否存在预测偏差或公平性问题。

（完）
