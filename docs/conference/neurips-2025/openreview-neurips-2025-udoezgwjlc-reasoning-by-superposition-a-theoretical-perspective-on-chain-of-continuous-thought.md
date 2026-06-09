---
title: "Reasoning by Superposition: A Theoretical Perspective on Chain of Continuous Thought"
title_zh: 叠加推理：连续思维链的理论视角
authors: "Hanlin Zhu, Shibo Hao, Zhiting Hu, Jiantao Jiao, Stuart Russell, Yuandong Tian"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=UdOEZgWJLc"
tags: ["query:graph-llm"]
score: 9.0
evidence: 证明两层Transformer结合连续思维链可解决有向图可达性问题
tldr: 针对连续思维链相比离散思维链在图推理等任务上优势的理论空白，从理论上证明两层Transformer结合连续协同可解决有向图可达性问题，为理解大语言模型的图推理能力奠定理论基础，揭示了连续表示在复杂推理中的潜力。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-udoezgwjlc/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1252, \"height\": 242, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-udoezgwjlc/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1277, \"height\": 358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-udoezgwjlc/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1218, \"height\": 332, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-udoezgwjlc/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 428, \"height\": 431, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-udoezgwjlc/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1442, \"height\": 613, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-udoezgwjlc/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 684, \"height\": 580, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-udoezgwjlc/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1317, \"height\": 323, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-udoezgwjlc/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 898, \"height\": 248, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-udoezgwjlc/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1189, \"height\": 497, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-udoezgwjlc/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 507, \"height\": 535, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-udoezgwjlc/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 690, \"height\": 217, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-udoezgwjlc/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1450, \"height\": 242, \"label\": \"Table\"}]"
motivation: 连续思维链在图可达性等任务上表现优于离散版本，但缺乏理论解释。
method: 通过构造理论证明，展示两层Transformer加连续协同可解有向图可达问题。
result: 证明了该架构下连续步骤能准确求解图可达性。
conclusion: 为连续思维链在图推理中的有效性提供了理论支撑。
---

## Abstract
Large Language Models (LLMs) have demonstrated remarkable performance in many applications, including challenging reasoning problems via chain-of-thought (CoT) techniques that generate ``thinking tokens'' before answering the questions. While existing theoretical works demonstrate that CoT with discrete tokens boosts the capability of LLMs, recent work on continuous CoT lacks a theoretical understanding of why it outperforms discrete counterparts in various reasoning tasks, such as directed graph reachability, a fundamental graph reasoning problem that includes many practical domain applications as special cases. In this paper, we prove that a two-layer transformer with $D$ steps of continuous CoT can solve the directed graph reachability problem, where $D$ is the diameter of the graph, while the best known result of constant-depth transformers with discrete CoT requires $O(n^2)$ decoding steps where $n$ is the number of vertices ($D<n$). 
In our construction, each continuous thought vector is a superposition state that encodes multiple search frontiers simultaneously (i.e., parallel breadth-first search (BFS)), while discrete CoT must choose a single path sampled from the superposition state, which leads to a sequential search that requires many more steps and may be trapped in local solutions.
We also performed extensive experiments to verify that our theoretical construction aligns well with the empirical solution obtained via training dynamics. Notably, encoding of multiple search frontiers as a superposition state automatically emerges in training continuous CoT, without explicit supervision to guide the model to explore multiple paths simultaneously.

---

## 论文详细总结（自动生成）

好的，作为一名资深学术论文分析助手，我将使用中文，以 Markdown 格式，对您提供的论文《Reasoning by Superposition: A Theoretical Perspective on Chain of Continuous Thought》进行结构化、深入、客观的总结。

### 1. 论文的核心问题与整体含义

*   **研究动机与背景**：
    *   大语言模型（LLM）在结合思维链（CoT）技术后，推理能力显著提升。现有理论工作已经证明了在文本空间生成离散“思考token”的CoT如何增强Transformer的表达能力。
    *   然而，近期提出的“连续思维链”（Continuous CoT, 如 COCONUT 方法）在诸如**有向图可达性**等复杂推理任务上，表现优于离散CoT，但**其背后的理论机制尚不清楚**。一个关键观察是，连续思维似乎能同时编码多个候选推理路径。
*   **核心问题**：
    *   **连续思维链为何比离散思维链更强大？** 其表达能力的根本来源是什么？
*   **整体含义**：
    *   本文首次从理论上证明，连续思维链的强大之处在于其能将中间推理状态表示为一种“**叠加态**” (Superposition State)，从而在单个自回归步骤中隐式地执行**并行搜索**（如广度优先搜索 BFS），而离散思维链则被迫选择单一路径进行串行搜索，效率低下且可能陷入局部解。这为理解和改进LLM的推理能力提供了全新的理论基础。

### 2. 论文提出的方法论

*   **核心思想**：
    *   **叠加态推理**：论文的核心贡献在于揭示，连续思维向量并非一个确定的点，而是可以同时表示多个有效的搜索前沿（如在图搜索中，同时代表多个可达节点）。这类似于量子力学中的“叠加态”。离散CoT的每个token则是这种叠加态的“坍缩”，从而丧失了并行性。
*   **关键技术细节（理论构建）**：
    *   论文针对**有向图可达性问题**，构造了一个具体的两层Transformer模型，并证明了其能力。关键构建模块和流程如下：
        1.  **文本格式**：图数据（边）、查询（起始节点、两个候选目标节点）被序列化为token序列输入。
        2.  **注意力选择器 (Attention Chooser)**：这是基础构建块。通过精心设计的查询（Q）和键（K）矩阵，使模型能根据当前位置的token类型（如边、特殊符号），精确地关注到序列中的相对位置（如边的源节点或目标节点）。
        3.  **第一层Transformer**：
            *   **多头注意力**：利用5个“注意力选择器”头，将每条边 `<e>` 对应的源节点 `s_i` 和目标节点 `t_i` 的嵌入，分别拷贝到该边token嵌入的两个缓冲区内。
            *   **MLP层**：充当滤波器，滤除softmax带来的微小注意力噪声，确保缓冲区内信息的纯净。
        4.  **第二层Transformer**：
            *   **注意力机制（图搜索扩展）**：以当前的连续思维 `[t_c]` 作为查询。`[t_c]` 是所有在 `c` 步内从根节点可达的节点向量的**归一化叠加**。此时，`[t_c]` 会与所有边token的键（由源节点 `s_i` 构成）进行点积计算。只有当 `s_i` 是 `[t_c]` 叠加态中的一部分时，点积才为正。这样，注意力机制就将所有以 `[t_c]` 中节点为起点的边的目标节点 `t_i` 聚拢起来，实现了**一步图搜索扩展**。
            *   **MLP层（等权化与去噪）**：对聚合后的向量进行过滤和权重平整，得到新的连续思维 `[t_{c+1}]`，即所有在 `c+1` 步内可达的节点的归一化叠加态。
        5.  **最终预测（测量）**：经过 `D` 步（`D` 为图直径）连续思维后，输入特殊的 `<A>` token。该token的注意力会“测量”最终的叠加态 `[t_D]`，比较两个候选目标节点 `c1` 和 `c2` 在叠加态中的信号强度，并预测信号更强的那个为可达节点。
*   **公式/算法流程**：
    *   核心的连续思维迭代表达式为：`[t_{c+1}] = TF_θ(h_{[t0]}, [t_1], ..., [t_c])`。
    *   理论证明的核心是：如果当前 `[t_c] = (1/√|V_c|) * Σ_{v∈V_c} u_v`，则经过上述构造的两层Transformer后，下一状态的 `[t_{c+1}] = (1/√|V_{c+1}|) * Σ_{v∈V_{c+1}} u_v`。其中 `V_c` 是 `c` 步内可达的节点集合，`u_v` 是节点 `v` 的嵌入向量。

### 3. 实验设计

*   **数据集/场景**：
    *   使用 **ProsQA** 数据集的子集，该数据集包含需要3-4步推理的有向图问题。图节点作为专用tokens注入词表。
*   **Benchmark与对比方法**：
    *   **COCONUT (Continuous CoT)**：核心方法，使用2层、768维、8个注意力头的GPT-2风格解码器，从头训练。
    *   **CoT (Discrete CoT)**：标准文本思维链，使用与COCONUT相同规模的模型。
    *   **No CoT**：不进行任何思维链推理，直接预测。
    *   **CoT\***：一个更大规模的离散CoT模型（12层，12个注意力头），作为增强基线。
*   **训练方法**：
    *   采用多阶段课程学习。第 `i` 阶段教会模型在生成 `i` 个连续思考向量后，预测思维链中的第 `i` 个节点。超过解决方案长度后，则直接学习预测最终答案。

### 4. 资源与算力

*   文中明确提到，在附录C.3部分，每次COCONUT实验运行大约需要**24小时**，使用了**两块Nvidia A100 80GB GPU**。

### 5. 实验数量与充分性

*   **主要实验**：
    *   **性能对比**：报告了COCONUT、CoT (2层)、CoT\* (12层) 和 No CoT 在ProsQA上的总体准确率。结果显示COCONUT接近完美，大幅领先所有基线。
    *   **可视化分析**：
        *   **注意力模式**：可视化了第一层和第二层的注意力图，验证了第一层模型的“拷贝”行为和第二层模型的“前沿扩展”行为。
        *   **潜在思维表示分析**：计算了连续思维向量与不同类别节点（不可达、可达、前沿、最优）嵌入的内积，验证了叠加态的并行编码特征。
        *   **探索优先级分析**：分析了模型是否会自动偏向于关注通向最优解的“前沿”与“最优”路径。
    *   **稳定性与消融实验**：
        *   使用**3个随机种子**重复实验，并报告了潜在表示内积的均值和标准差，验证了叠加搜索行为的稳定性。
        *   引入了**COCONUT-BFS**训练策略（监督信号改为从第 `i` 步前沿节点中**均匀随机采样**，而非只给最优路径），结果表明模型仍能学习到类似的并行搜索策略，且性能没有下降，这消除了训练信号偏差带来搜索行为的疑虑。
*   **充分性与客观性**：实验设计非常严谨。不仅有宏观性能对比，还深入到模型内部进行机制的详尽验证和可视化。通过多随机种子和改变训练策略的消融实验，证明了结果的鲁棒性，排除了对特定训练技巧的依赖。评估客观、公平。

### 6. 论文的主要结论与发现

*   两层Transformer结合 `D` 步连续思维链可以解决 `D`-直径有向图的可达性问题，而离散CoT至少需要 `N^2` 步。
*   连续思维的本质是 **“叠加态”** ，可以在单个推理步骤中**并行模拟广度优先搜索**。
*   离散思维是叠加态的“坍缩”，强迫模型进行串行的深度优先搜索，效率较低。
*   这种叠加态搜索行为是**从梯度下降训练中自动涌现**的，无需显式地指导模型去探索多条路径。

### 7. 优点

*   **理论贡献深刻**：首次为连续思维链的优越性提供了坚实的理论基础，揭示了“叠加态”并行推理这一优美机制。
*   **理论-实验高度结合**：理论构造在实验中得到了完美的验证和复现，形成了强有力的证据闭环。
*   **实验分析细致**：不仅看最终成绩，更深入解剖模型“大脑”的注意力机制和潜在空间表示，解释性极强。
*   **消融实验巧妙**：通过改变训练目标的COCONUT-BFS实验，有力地排除了训练偏差，证明了叠加搜索行为的鲁棒性。
*   **构造通用性强**：不同于以往很多理论工作构造的问题特定或长度特定的位置编码，本文的构造适用于正弦位置编码等通用实践。

### 8. 不足与局限

*   **问题域的特定性**：理论证明和实验验证目前主要局限在**有向图可达性**这一特定问题上。向更广泛的推理任务（如数学、规划）的推广需要更多研究。
*   **模型规模有限**：实验使用的模型相对较小（2层），尽管这正呼应了理论构造，但在更大规模、更通用LLM（如预训练大模型）上进行微调并验证该机制，是重要的下一步。
*   **缺乏对训练动态的理论解释**：论文留下了一个开放性问题，即为什么监督信号仅给出最优路径时，模型仍能学到并行的广度优先搜索策略，而不是更简单的贪心搜索，其训练动力学尚不明确。
*   **理论下界缺失**：论文证明了连续CoT的上界，但尚未给出离散CoT在该问题上所需步数的严格理论下界，无法彻底展示两者在表达能力上的绝对分离。

（完）
