---
title: "From Sequence to Structure: Uncovering Substructure Reasoning in Transformers"
title_zh: 从序列到结构：揭示 Transformer 的子结构推理
authors: "Xinnan Dai, Kai Yang, Jay Revolinsky, Kai Guo, Aoran Wang, Bohang Zhang, Jiliang Tang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=1Qo6DzdPOG"
tags: ["query:graph-llm"]
score: 9.0
evidence: 通过诱导子结构过滤分析仅解码器变换器如何从文本中理解图结构
tldr: 针对大语言模型如何从文本描述中理解图结构这一核心问题，该论文以子结构提取切入，提出诱导子结构过滤（ISF）视角，从理论和实验两方面揭示了多层变换器识别子结构的内在机理。研究澄清了输入查询的影响，为解释和改进 LLM 的图推理能力提供了可解释的理论框架。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-1qo6dzdpog/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1441, \"height\": 370, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1qo6dzdpog/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 718, \"height\": 429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1qo6dzdpog/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 361, \"height\": 434, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1qo6dzdpog/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 327, \"height\": 379, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1qo6dzdpog/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 352, \"height\": 358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1qo6dzdpog/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 351, \"height\": 355, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1qo6dzdpog/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 712, \"height\": 291, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1qo6dzdpog/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 434, \"height\": 382, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1qo6dzdpog/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 244, \"height\": 358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1qo6dzdpog/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 403, \"height\": 320, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-1qo6dzdpog/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1450, \"height\": 296, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1qo6dzdpog/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1447, \"height\": 167, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1qo6dzdpog/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 824, \"height\": 329, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1qo6dzdpog/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 495, \"height\": 321, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1qo6dzdpog/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1454, \"height\": 394, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1qo6dzdpog/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1188, \"height\": 136, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1qo6dzdpog/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 782, \"height\": 217, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1qo6dzdpog/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1454, \"height\": 330, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1qo6dzdpog/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1444, \"height\": 538, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1qo6dzdpog/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 839, \"height\": 219, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1qo6dzdpog/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 930, \"height\": 258, \"label\": \"Table\"}]"
motivation: 尽管 LLM 能执行图推理任务，但其内部如何从文本中理解图结构仍不清楚。
method: 以子结构提取任务为对象，提出诱导子结构过滤（ISF）视角，结合实证与理论分析揭示多层变换器内部机制。
result: ISF 有效捕获了变换器中的子结构识别过程，并阐明了输入查询的影响。
conclusion: 该研究为 LLM 的图推理能力提供了机理性解释，有助于设计更强大的图推理模型。
---

## Abstract
Recent studies suggest that large language models (LLMs) possess the capability to solve graph reasoning tasks. Notably, even when graph structures are embedded within textual descriptions, LLMs can still effectively answer related questions. This raises a fundamental question: How can a decoder-only Transformer architecture understand underlying graph structures? To address this, 
we start with the substructure extraction task, interpreting the inner mechanisms inside the transformers and analyzing the impact of the input queries. Specifically, through both empirical results and theoretical analysis, we present Induced Substructure Filtration (ISF), a perspective that captures the substructure identification in the multi-layer transformers. We further validate the ISF process in LLMs, revealing consistent internal dynamics across layers. Building on these insights, we explore the broader capabilities of Transformers in handling diverse graph types. Specifically, we introduce the concept of thinking in substructures to efficiently extract complex composite patterns, and demonstrate that decoder-only Transformers can successfully extract substructures from attributed graphs, such as molecular graphs. Together, our findings offer a new insight on how sequence-based Transformers perform the substructure extraction task over graph data.

---

## 论文详细总结（自动生成）

好的，作为一名资深学术论文分析助手，我将以 Markdown 格式，对论文《From Sequence to Structure: Uncovering Substructure Reasoning in Transformers》进行结构化、深入、客观的总结。

### 1. 论文的核心问题与整体含义（研究动机和背景）

*   **核心问题**：大型语言模型（LLMs）的骨干——仅解码器（decoder-only）的 Transformer 架构，天生为处理序列化文本数据设计，它如何能从文本描述中理解并推理**图结构**这类非序列数据？
*   **研究动机**：现有研究对 LLM 图推理能力的解释多局限于寻找最短路径等**线性路径**任务。现实世界的图包含更复杂的非线性子结构（如环、树、特定基序）。因此，从路径发现任务中获得的解释可能无法推广到更全面的图理解。
*   **整体含义**：本工作旨在揭示 Transformer 如何应对更广泛的**子结构理解**挑战，特别聚焦于**子结构提取**任务。通过分析这一过程，为基于序列的 Transformer 如何处理图数据提供了新的视角和机理性解释。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

本研究的核心是为 Transformer 的图推理能力提供一个可解释的理论框架，主要通过以下方法实现：

*   **任务抽象与简化**：
    *   **输入**：将图表示为文本序列（如邻接表 `Adjacency List, AL` 或边列表 `Edge List, EL`），并将问题提示词编码为符号 token。两者拼接构成输入查询 `Q`。
    *   **输出**：要求模型提取出与查询匹配的同构子图，并输出构成子图的节点ID序列。
*   **内部机制解释：诱导子结构过滤 (Induced Substructure Filtration, ISF)**
    *   **核心思想**：ISF 是一个用于解释多层 Transformer 如何逐步识别子结构的视角。它假设 Transformer 执行一种**逐层的节点聚合过程**。
    *   **理论模型**：该过程被形式化为 **k-Node m-Filtration (k节点m步过滤)**。
        *   `k` 指目标子结构包含的节点数。
        *   `m` 指模型识别该子结构所需的“聚集”步骤数（通常对应 Transformer 的层数）。
        *   每一过滤步骤对应一个诱导子图 `G'[V'_i]`，其中 `V'_1 ⊂ ... ⊂ V'_m` 是逐步扩大的节点集合。
    *   **理论保证**：通过定义**子图同构指示张量**，论文从理论上证明了（Theorem 3.3, 3.5, 3.8, 3.10）：具有恒定深度、`O(n^k)` 隐藏维度的 Transformer 能够在每一层逐步计算出指示张量，并最终在各种复杂情况（单/多数量、单/多形状子结构）下提取出匹配的顶点元组。
*   **对复杂图的扩展方法：Thinking in Substructures (Tins)**
    *   **核心思想**：为了高效处理复杂组合模式，Tins 方法模仿了推理语言模型的行为，即**将一个复杂的子结构分解为多个更简单的组成子结构（分步子结构）进行搜索**。
    *   **算法流程**：模型输出不再直接给出最终答案，而是先生成各分步子结构的集合 `{P1}, {P2}, ..., {Pt}`，再用特殊 token `<ANS>` 引导，最后输出最终的子结构 `ANS(Ĝ)`。这从理论上将提取复杂度从 `O(n^k)` 降低到了 `O(n^q)`，其中 `q` 是最大分步子结构的尺寸，且 `q < k`。

### 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法

*   **数据集**：
    *   **合成图数据集**：自己生成超过 500 万个有向图，节点数从 4 到 16，边数从 3 到 120。严格保证训练集和测试集的图是非同构的，以防答案复制。
    *   **分子图数据集**：使用了来自 QM9（134k 分子）和 PCBA（440k 分子）的真实世界分子图数据，用于验证带属性图的子结构提取。
*   **测试场景与基准 (Benchmark)**：
    *   **单形状-单数量 (Single-Shape-Single-Num)**：从图中提取一个特定形状的子结构（如三角形、正方形、五边形、房屋形等）。
    *   **单形状-多数量 (Single-Shape-Multi-Num)**：从图中提取所有匹配特定形状的子结构（最多5个）。
    *   **多形状-单数量 (Multi-Shape-Single-Num)**：从包含不同形状子结构的混合图中，根据提示提取目标形状。
    *   **输入查询影响**：对比了 `Adjacency List` 和 `Edge List` 两种图文本表示，以及术语式和拓扑式两种问题提示词的效果。
    *   **复杂图理解**：
        *   **组合子结构**：验证 **Tins** 方法在提取如“对角线+三角形”等组合模式上的性能提升。
        *   **带属性图**：在分子图上识别官能团（如羟基、羧基、苯环），作为带属性图提取的基准。
*   **对比方法**：本研究主要目标是**机制解释与验证**，而非模型性能比拼。因此，其“对比”主要体现在：
    *   **不同配置下的自对比**：对比不同层数、训练数据量、输入格式、提示词类型、是否使用Tins等方法对**同一类Transformer模型**（轻量级GPT-2）性能的影响。
    *   **LLM 行为验证**：通过可视化 LLaMA 3.1-8B-Instruct 模型的内部 token 嵌入，对比其内部动态是否与从零训练的 Transformer 呈现的 ISF 过程一致。

### 4. 资源与算力

*   **算力资源**：文中明确指出，所有实验均在配备 **8 块 NVIDIA A6000 GPU** 的机器上进行。
*   **训练时长**：论文未明确提及具体的训练总时长。
*   **模型规模**：
    *   **从零训练的 Transformer**：基于 GPT-2 架构的轻量级版本，隐藏层维度为 **384** 或 **192**，层数根据任务在 2 到 5 层之间变化。
    *   **LLM 实验**：使用 **LLaMA 3.1-8B-Instruct** 进行微调和可视化。

### 5. 实验数量与充分性：大概做了多少组实验

*   **实验数量与组别**：实验设计非常丰富，涵盖了多个维度的系统性评估：
    1.  **9种不同子结构**（表1）在4种训练数据量（100K~400K）和4种模型层数（2~5）下的提取性能（至少 `9 * 4 * 4` 组实验）。
    2.  **单/多数量、单/多形状**的多种场景评估（图4, 5, 6）。
    3.  **输入表示**：对比了 `AL` 和 `EL` 在提取不同子结构时的性能。
    4.  **问题提示**：对比了2种术语、4种拓扑描述及其符号级/令牌级扰动性能（表2）。
    5.  **可视化分析**：对从零训练的 Transformer 和 LLM 进行了多层嵌入可视化（如 t-SNE 图，ARI/NMI 评分曲线）。
    6.  **复杂图扩展**：`Tins` 方法在4种组合子结构上的消融实验（表3），以及分子图在3种官能团及混合训练下的实验（表4）。
*   **充分性与客观性**：
    *   **充分性**：实验非常充分。系统地探索了影响子结构提取的多个核心因素（模型深度、数据量、结构复杂性、输入格式），并通过可视化将经验观察与理论模型紧密联系起来，论证链完整。
    *   **客观性**：实验设置客观公正。采用合成数据精确控制变量，避免了真实数据中不可控因素的干扰。使用严格的“完全匹配准确率”作为评估指标，保证了评判的客观性。

### 6. 论文的主要结论与发现

*   **ISF 是 Transformer 的通用推理机制**：仅解码器 Transformer 求解子结构提取任务是通过逐层的**诱导子结构过滤 (ISF)** 过程实现的。该过程在理论上和实践中均得到了验证，并且也反映在 LLM (LLaMA 3.1) 的内部状态中，说明这是一种通用的内在机制。
*   **模型深度与子结构复杂度强相关**：提取某个子结构所需的最小 Transformer 层数，与该子结构的**节点数**密切相关。节点越多，所需层数通常越多。
*   **图表示和提示词影响显著**：
    *   `Adjacency List (AL)` 在效率上优于 `Edge List (EL)`，但在理论上都能表达图的邻接矩阵。
    *   Transformer 更倾向于将问题提示中的术语或特定 token 作为抽象概念来指导提取，而非完全理解拓扑结构再映射回原图。
*   **Thinking in Substructures (Tins)** 是一种有效策略：通过将复杂子结构分解为简单分步，模型的提取能力得到显著提升，尤其能在有限训练数据下大幅提高性能。
*   **模型具有处理属性图的潜力**：在分子图上的实验表明，Transformer 能够成功扩展其子结构提取能力到带属性的图中，前提是每个节点能通过其特征被唯一确定。

### 7. 优点：方法或实验设计上有哪些亮点

*   **新颖的解释性视角**：提出了**ISF** 这一全新的视角来解释 Transformer 的图推理机制，比此前局限于“路径搜索”的理解更深刻和通用。
*   **理论与实证紧密结合**：不仅提出理论概念（如 k-Node m-Filtration），还通过定理证明其可行性，并通过多层 token 嵌入的可视化进行实证验证，论证严谨性很高。
*   **系统性的实验控制**：利用大规模合成图数据，可以精确地控制图的尺寸、子结构类型、数量、输入格式等变量，从而排除无关因素，得出可靠的因果性结论。
*   **从解释到改进**：从 ISF 机制出发，衍生出 **Thinking in Substructures (Tins)** 这一提升复杂推理能力的方法，体现了“理解机制 -> 改进方法”的良性研究路径。

### 8. 不足与局限：包括实验覆盖、偏差风险、应用限制等

*   **任务类型的局限性**：研究主要聚焦于**子结构提取**任务。虽然它是一个核心图推理任务，但不足以完全覆盖 LLM 在图上的所有能力（如节点分类、链接预测、图级别的性质判断等）。
*   **图规模与结构类型的局限**：
    *   **图规模有限**：实验中使用的合成图节点数相对较小（4-16）。对于大型图的扩展性未作探讨。
    *   **图类型单一**：主要使用有向图，虽然涉及带属性图（分子图），但对于权重图、动态图、异构图等更复杂的图结构，其结论的泛化性有待验证。
*   **模型规模与训练环境的差距**：实验主要基于从零训练的轻量级 Transformer 和对特定 LLM 的微调。基于自回归预训练的大模型与从零训练的小模型在内部机制上是否完全等价，以及 ISF 在更大规模、未经微调的 LLM 中如何体现，仍需进一步探索。
*   **理论分析的简化**：理论分析（如隐藏层维度 `O(n^k)` 的要求）是基于“对数精度”假设的，距实际模型部署有较大差距。理论上对输入表示等效的阐述，未能完全解释实践中 EL 性能较差的现象，仍需经验层面的补充分析。

（完）
