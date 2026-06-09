---
title: "GraphChain: Large Language Models for Large-scale Graph Analysis via Tool Chaining"
title_zh: "GraphChain: 通过工具链实现大规模图分析的大语言模型"
authors: "Chunyu Wei, Wenji Hu, Xingjia Hao, Xin Wang, Yifan Yang, Yunhai Wang, Yang Tian, Yueguo Chen"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=Rdz6ESQYkK"
tags: ["query:graph-llm"]
score: 9.0
evidence: LLM通过工具链和强化学习分析大规模图
tldr: 针对大语言模型分析大规模图时上下文受限和推理僵化的问题，本文提出GraphChain框架，通过强化学习生成动态工具链，并结合结构感知测试时自适应，有效扩展LLM的图分析能力。实验表明该方法能处理大规模图，提升分析性能。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdz6esqykk/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1434, \"height\": 650, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdz6esqykk/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1441, \"height\": 688, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdz6esqykk/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 640, \"height\": 627, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdz6esqykk/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 789, \"height\": 656, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdz6esqykk/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1143, \"height\": 354, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdz6esqykk/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1426, \"height\": 1223, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdz6esqykk/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1391, \"height\": 1289, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdz6esqykk/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1459, \"height\": 474, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdz6esqykk/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1459, \"height\": 544, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdz6esqykk/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 876, \"height\": 151, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdz6esqykk/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1160, \"height\": 202, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdz6esqykk/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1013, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdz6esqykk/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 875, \"height\": 216, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdz6esqykk/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1451, \"height\": 553, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdz6esqykk/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1346, \"height\": 1643, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdz6esqykk/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1346, \"height\": 1593, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdz6esqykk/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1347, \"height\": 1769, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdz6esqykk/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1349, \"height\": 1115, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdz6esqykk/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1388, \"height\": 1442, \"label\": \"Table\"}]"
motivation: 大语言模型因上下文限制难以直接分析大规模图，现有方法推理僵化。
method: 提出GraphChain，利用强化学习生成图蒸馏工具序列，并引入结构感知测试时自适应。
result: GraphChain有效扩展LLM的大规模图分析能力，性能优于基线。
conclusion: 该框架为LLM在图分析中的应用提供了新途径。
---

## Abstract
Large Language Models (LLMs) face significant limitations when applied to large-scale graphs, struggling with context constraints and inflexible reasoning. We introduce GraphChain, a novel framework enabling LLMs to analyze large graphs by orchestrating dynamic sequences of specialized tools, mimicking human exploratory processes. GraphChain incorporates two core technical contributions: (1) Progressive Graph Distillation, a reinforcement learning approach that learns to generate tool sequences balancing task relevance and intermediate state compression, thereby overcoming LLM context limitations. (2) Structure-aware Test-Time Adaptation (STTA), a mechanism using a lightweight, self-supervised adapter conditioned on graph spectral properties to efficiently adapt a frozen LLM policy to diverse graph structures via soft prompts without retraining. Experiments show GraphChain significantly outperforms prior methods, enabling scalable and adaptive LLM-driven graph analysis.

---

## 论文详细总结（自动生成）

好的，作为资深学术论文分析助手，我将对论文《GraphChain: Large Language Models for Large-scale Graph Analysis via Tool Chaining》进行结构化、深入、客观的总结。

# GraphChain 论文深度分析总结

### 1. 论文的核心问题与整体含义

*   **核心问题**：大语言模型在分析大规模图数据（如社交网络、金融交易网络）时面临两大根本性挑战：
    *   **上下文耗尽**：图数据的规模（如数百万节点和边）远超LLM的上下文窗口限制，无法被完整加载和直接处理。
    *   **推理僵化**：现有的“LLM+工具”方法通常采用单步工具调用，让模型单纯“生成”API调用，缺乏对复杂问题进行多步、渐进式探索的能力，导致在面对需要组合多种分析操作的复杂任务时产生“推理幻觉”。
*   **整体含义**：本文的核心思想是，有效的图分析应像人类探索未知领域一样，是一个由粗到细、逐步深入、自适应调整的**序贯决策过程**。基于此，作者提出**GraphChain框架**，让LLM充当“大脑”，通过强化学习生成并执行一串图处理工具，以解决大图分析问题。

### 2. 论文提出的方法论

GraphChain框架将大规模图分析建模成一个马尔可夫决策过程，并通过两大核心技术来解决训练和适应性问题。

*   **核心思想：动态工具链**
    *   给定一个复杂的图分析查询，GraphChain不试图一次性得出答案，而是指导LLM逐步选择并执行一个由专业图处理函数（基于NetworkX库）组成的序列。每一步操作都基于前一步的结果，逐步聚焦到图中与任务相关的关键部分。

*   **关键技术细节**
    *   **1) 渐进式图蒸馏**
        *   **问题**：在指数级增长的可能的工具序列中搜索最优解是困难的。
        *   **方法**：作者设计了一个专门的**强化学习奖励函数**，引导智能体（LLM）在每一步选择工具时，不仅要考虑其与任务的最终相关性，还要积极**缩减中间状态的信息量**。
        *   **量化指标**：提出了**图描述长度 (GDL)**来衡量当前图状态的数据量，以及**任务相关性 (Rel)** 来评估当前状态对回答查询的效用。奖励函数鼓励每一步操作能同时增加相关性并减少GDL。
        *   **信息论视角**：从信息瓶颈原则出发，这一机制等价于引导LLM在每一步的操作中，尽可能保留任务相关信息，同时丢弃与任务无关的噪音信息，从而逐步将大规模图压缩到LLM可以最终处理的、最关键的子图。
        *   **优化算法**：采用**近端策略优化 (PPO)**算法，并结合广义优势估计 (GAE) 来稳定训练过程。

    *   **2) 结构感知的测试时自适应 (STTA)**
        *   **问题**：真实世界的图数据分布多样（社交网络、引文网络等拓扑结构差异巨大），对每个新图都重新训练模型成本过高。
        *   **方法**：设计了一个轻量级的**适配器网络 (Aψ)**，该网络不直接改变LLM参数，而是根据目标图的结构特征生成一个**软提示词 (Soft Prompt)**。
        *   **结构指纹**：为了避免计算开销，通过计算图的归一化拉普拉斯矩阵的少数**最小奇异值**作为该图的“结构指纹 (zG)”，这个紧凑的向量能有效捕获图的宏观拓扑属性。
        *   **自监督适应**：在测试新图时，使用一个通用LLM生成一些与该图相关的辅助查询，然后通过**自监督的 REINFORCE 算法**来优化适配器参数。优化目标是找到一个软提示词，使得冻结的LLM策略在解决这些辅助查询时，能产生**更短的工具链（更高效）**，同时不**偏离原有策略太远（通过KL散度约束）**，从而实现对特定图结构的快速适配。

### 3. 实验设计

*   **数据集/场景**：实验覆盖了五种不同领域的真实图数据集，以验证方法的通用性：
    *   **金融网络：** Elliptic (比特币交易图，约20万节点)
    *   **化学分子：** QM9
    *   **社交网络：** Facebook, Twitter
    *   **引文图：** Cora, CiteSeer, PubMed
    *   **交通网络：** METR-LA

*   **对比基准 (Baseline)**：比较方法分为两类，对比全面且具有较强的竞争性：
    *   **纯文本指令方法**：包括闭源大模型 (GPT-4o, Claude-4-Sonnet 等)、专用图推理模型 (GraphWiz, NLGraph)。这些方法将图转化为文本描述输入LLM。
    *   **工具指令方法**：Graph-ToolFormer, GraphForge, ToolGen 等最新的将API调用与LLM结合的方法。
    *   *注意：为确保公平比较，在进行性能对比时，所有图被分割为100个节点以下的子图。*

*   **自身变体 (消融实验)**：
    *   `w/o graph distillation` (移除渐进式图蒸馏)
    *   `w/o test-time adaptation` (移除测试时自适应)

*   **其他实验维度**：
    *   **可扩展性分析**：在不同的图规模（高达20万节点）和查询复杂度（所需工具步数）下测试性能。
    *   **迁移学习评估**：在一个领域（金融网络）上训练，在其它未见领域（社交、引文、交通）上测试，检验泛化能力。
    *   **工具链分析与鲁棒性**：分析了在不同图上工具的使用模式，并测试了在移除50%工具后性能的下降情况，以评估鲁棒性。
    *   **不同基座模型鲁棒性**：测试了在Qwen2.5, Llama3.1, GLM4等不同基座LLM上的表现，并对比了Qwen2.5不同参数量级的模型。

### 4. 资源与算力

*   **硬件**：所有实验均在**2块 NVIDIA A800 (80GB) GPU** 上完成。
*   **基座模型**：主要使用 **Qwen2.5-7B-Instruct** 作为基座LLM进行微调。
*   **微调方法**：采用 **LoRA** 技术进行参数高效微调。
*   **训练时长**：文中有提到训练轮次等细节，但未明确给出总训练时长。

### 5. 实验数量与充分性

实验设计**非常全面、充分且客观**，具体体现在：
*   **领域广泛**：涵盖了5个截然不同的真实图场景，并从文本和工具两个角度对比了多达10种以上的强大基线模型，确保了结论的普适性。
*   **对比公平**：充分考虑了基线模型的输入限制（如上下文长度），通过分割子图的方式保证了对比的公平性。
*   **分析深入**：不仅报告了整体性能，还通过消融实验、可扩展性、迁移能力、对基座模型和工具集的鲁棒性等多维度分析，深刻揭示了GraphChain各组件的作用和模型的泛化能力。统计显著性也通过t检验进行了验证。
*   **结论可靠**：丰富的实验维度使得每一个结论都有坚实的实证支撑，实验设计严格遵循了科学严谨性。

### 6. 论文的主要结论与发现

*   **性能显著提升**：GraphChain在所有五种图场景中都显著优于现有最强基线，平均准确率提升**20.7%**，达到**84.7%**。
*   **卓越的可扩展性**：GraphChain能有效处理高达**200,000个节点**的大图，而其他方法的性能会随着图的增大和查询复杂度的增加而急剧下降，显示出其解决上下文耗尽问题的强大能力。
*   **高效参数利用率**：仅使用7B参数的模型，其性能便超越了200B参数的通用大模型（GPT-4o）和同级别的专用模型，证明了其极高的效率。
*   **关键组件作用**：消融实验证实，*渐进式图蒸馏*和*结构感知测试时自适应* 都是提升性能的关键，其中图蒸馏的作用尤为突出。
*   **强大的泛化能力**：在单一图领域训练后，结合STTA模块，GraphChain能够以较小的性能损失泛化到其他未见过的图领域，实现了模型复用。
*   **自适应策略**：在不同类型图上，GraphChain学习到了差异化的工具使用模式（如交通网络多用路径规划，社交网络多用中心度度量），表明其能根据图的结构特性自适应地调整分析策略。

### 7. 优点

*   **思想创新**：将图分析建模为序贯探索过程，由粗到精逐步聚焦，完美地模拟了人类专家的分析逻辑，为解决LLM上下文限制问题提供了优雅的思路。
*   **技术扎实**：巧妙结合了**信息瓶颈理论（图蒸馏）**、**谱图理论（结构指纹）** 和**元学习/自适应思想（STTA）**，设计了两个原理清晰且有效的技术模块。将奖励函数的设计与信息论原则对齐，理论支撑强。
*   **系统设计完善**：生成的中间结果通过简洁的自然语言摘要传递给LLM，而非直接压缩子图，这是工程上非常聪明且高效的处理方式。
*   **实验极其详尽**：广泛的场景、全面的基线、多维度的分析和机制验证，使得这篇论文的论点非常有说服力。
*   **实用性强**：STTA机制使得模型无需为每个新图重新训练，显著降低了实际部署的成本和门槛，增强了框架的实用性。

### 8. 不足与局限

*   **对工具库的依赖**：框架的能力受限于预定义的NetworkX函数库。虽然实验证明了其对工具削减的鲁棒性，但其本质上仍无法解决库内不存在对应函数的全新任务。库的质量和覆盖度直接影响其能力上限。
*   **动态图、异质图等的处理**：论文指出当前主要关注于“静态图”，对于随时间演变的动态图、包含多种类型节点和边的异质图等更复杂的结构，可能需要进一步适配。
*   **LLM推理开销**：工具链的生成需要LLM进行多步推理和文本生成，这会带来额外的推理时间和计算成本。虽然可以用更小的LLM，但相比于纯算法方案，延迟仍是需要考虑的因素。
*   **“结构指纹”的局限性**：使用最小的奇异值捕捉全局拓扑虽然高效，但可能丢失对某些特定局部结构（如模体、特定的子图模式）敏感的细节信息，这可能会影响对图中微观模式的分析任务。

（完）
