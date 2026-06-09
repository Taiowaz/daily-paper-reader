---
title: "Attention Mechanisms Perspective: Exploring LLM Processing of Graph-Structured Data"
title_zh: 注意力机制视角：探索大语言模型对图结构数据的处理
authors: "Zhong Guan, Likang Wu, Hongke Zhao, Ming He, Jianping Fan"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=16oBNUlWyB"
tags: ["query:graph-llm"]
score: 10.0
evidence: 探索LLM如何处理图结构数据
tldr: 本文从注意力机制的视角出发，系统地探究了大语言模型（LLM）如何处理图结构数据。由于图数据强调拓扑连接，通常由GNN的消息传递机制建模，而LLM依赖自注意力，其有效性尚不明确。作者通过一系列实验，对比了LLM与GNN在图数据上的注意力行为，发现即使没有显式图结构约束，LLM也能通过注意力权重隐式捕捉节点间的关系，并在特定条件下展现出不错的图推理能力。然而，其性能仍不及专用GNN，揭示了注意力在处理固定拓扑时的局限性。这些发现为理解LLM的图推理潜力及未来融合GNN与LLM提供了实证指导，对设计图增强语言模型具有重要参考价值。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-16obnulwyb/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1767, \"height\": 551, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-16obnulwyb/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1761, \"height\": 544, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-16obnulwyb/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1770, \"height\": 859, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-16obnulwyb/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 673, \"height\": 447, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-16obnulwyb/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1708, \"height\": 920, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-16obnulwyb/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1725, \"height\": 642, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-16obnulwyb/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1762, \"height\": 1816, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-16obnulwyb/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1761, \"height\": 1790, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-16obnulwyb/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1761, \"height\": 1785, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-16obnulwyb/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1753, \"height\": 1752, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-16obnulwyb/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1733, \"height\": 1699, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-16obnulwyb/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1721, \"height\": 1698, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-16obnulwyb/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1772, \"height\": 1745, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-16obnulwyb/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1775, \"height\": 1712, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-16obnulwyb/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1775, \"height\": 1711, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-16obnulwyb/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1780, \"height\": 1550, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-16obnulwyb/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1778, \"height\": 1530, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-16obnulwyb/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1783, \"height\": 1513, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-16obnulwyb/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 895, \"height\": 276, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-16obnulwyb/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1640, \"height\": 274, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-16obnulwyb/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 877, \"height\": 502, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-16obnulwyb/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1772, \"height\": 595, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-16obnulwyb/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1209, \"height\": 406, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-16obnulwyb/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1206, \"height\": 404, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-16obnulwyb/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1620, \"height\": 274, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-16obnulwyb/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1621, \"height\": 275, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-16obnulwyb/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1456, \"height\": 317, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-16obnulwyb/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1759, \"height\": 393, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-16obnulwyb/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1756, \"height\": 393, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-16obnulwyb/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1757, \"height\": 396, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-16obnulwyb/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1683, \"height\": 1023, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-16obnulwyb/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1826, \"height\": 507, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-16obnulwyb/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1791, \"height\": 510, \"label\": \"Table\"}]"
motivation: 探究LLM的注意力机制在图结构数据上是否有效，是否可替代GNN的消息传递。
method: 从注意力机制视角进行实证研究，设计系列实验分析LLM对图拓扑的注意力模式。
result: 发现LLM能隐式捕捉图关系，但在固定拓扑上性能不及GNN，揭示了注意力的局限性。
conclusion: 为理解LLM的图推理能力提供了实证，对融合GNN与LLM具有指导意义。
---

## Abstract
Attention mechanisms are critical to the success of large language models (LLMs), driving significant advancements in multiple fields. However, for graph-structured data, which requires emphasis on topological connections, they fall short compared to message-passing mechanisms on fixed links, such as those employed by Graph Neural Networks (GNNs). This raises a question: ``Does attention fail for graphs in natural language settings?'' Motivated by these observations, we embarked on an empirical study from the perspective of attention mechanisms to explore how LLMs process graph-structured data. The goal is to gain deeper insights into the attention behavior of LLMs over graph structures. Through a series of experiments, we uncovered unique phenomena regarding how LLMs apply attention to graph-structured data and analyzed these findings to improve the modeling of such data by LLMs. The primary findings of our research are: 1) While LLMs can recognize graph data and capture text-node interactions, they struggle to model inter-node relationships within graph structures due to inherent architectural constraints. 2) The attention distribution of LLMs across graph nodes does not align with ideal structural patterns, indicating a failure to adapt to graph topology nuances. 3) Neither fully connected attention (as in LLMs) nor fixed connectivity (as in GNNs) is optimal; each has specific limitations in its application scenarios. Instead, intermediate-state attention windows improve LLM training performance and seamlessly transition to fully connected windows during inference. Source code: 
\href{https://anonymous.4open.science/r/LLM_exploration-B21F}{anonymous.4open.science/LLM\_exploration-B21F}

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义
- **核心问题**：探索大语言模型（LLM）在处理图结构数据时，其核心的注意力机制是否能够有效捕捉和利用图的拓扑连接信息。本文直接回应“为什么LLM在图任务上表现不如消息传递类的图神经网络（GNN）？”这一疑问。
- **研究动机**：LLM在诸多领域取得重大成功，但其在自然语言形式下处理图数据时效果不佳。注意力机制是LLM的基石，但在图数据中，对固定拓扑关系的建模需求与LLM的自注意力范式之间存在天然张力。因此，有必要从注意力机制的角度对LLM的图处理行为进行系统性实证研究，以揭示根本原因并指明改进方向。

### 2. 论文提出的方法论
本文并非提出一种新模型，而是设计了一套以注意力分析为核心的实证研究方法，从三个层次递进探索（对应文中Q1 - Q3）。
- **注意力分布分析（Q1）**：
  - **对比训练前后**：收集并可视化LLM（LLaGA微调的LLaMA2 - 7B）在节点令牌（node token）和文本令牌（text token）上的注意力分数分布，使用T检验、KS检验和JS散度验证分布变化。
  - **结构信息扰动实验**：构造四种递增的图连接破坏程度（从交换子节点到混合无关节点），观察模型性能下降趋势，并分析邻居 - 中心节点注意力变化。
- **注意力适应性分析（Q2）**：
  - **消除位置偏差**：通过固定长度的填充（padding）和随机打乱（random shuffling）输入指令，确保节点令牌具有固定位置，从而剥离序列位置对注意力的影响。
  - **可视化不同令牌间的注意力**：分别绘制节点→节点、文本→节点的注意力曲线，并与理想图拓扑重要性分布对比；绘制注意力热力图以识别特殊模式（如“Attention Sink”和“Skewed Line Sink”）。
- **注意力窗口分析（Q3）**：
  - **引入全局连通视野（GLH）**：定义度量k表示节点令牌在注意力窗口中的可见范围，k从0（仅自注意）到2L（全连通）。通过修改注意力掩码，将LLM的因果下三角矩阵约束为包含不同拓扑信息的部分连通图。
  - **多视角训练与迁移实验**：系统变化训练和推理时的k值（以及单向/双向），评估模型性能和跨视角迁移能力。

### 3. 实验设计
- **数据集**：
  - 异配图数据集：**Amazon-Ratings**、**Roman-Empire**（来自Platonov et al.）。
  - 同配图数据集：**PubMed**、**WikiCS**。
- **基线与配置**：
  - 基座模型：LLaMA2-7B、Vicuna-7B、LLaMA3-7B。
  - 图输入方式遵循LLaGA的指令微调范式，节点采样方案为8（一阶邻居）×8（二阶邻居）。
- **对比维度**：
  - 结构信息扰动：4个数据集 × 5种扰动水平（原始、I、II、III、IV）。
  - 注意力窗口：4个数据集 × 多种k值（k=1,2,3,4），以及单向（unidi）与双向（bidi）注意力。
  - 跨窗口迁移：训练用k值 vs 推理用k值的组合。
  - 额外基座模型验证（Vicuna-7B、LLaMA3-7B）和不同模板验证。

### 4. 资源与算力
- 文中明确提及使用了**LLaMA2-7B**、**Vicuna-7B**、**LLaMA3-7B**等模型进行实验。
- 提供了关键超参数（学习率1e - 4、warmup 0.05、梯度累积步数8、批大小4、训练1个epoch等）。
- **未明确说明**具体的GPU型号、数量以及单次实验的绝对训练时长。从使用7B模型和多个数据集、多组实验来看，所需算力规模中等。

### 5. 实验数量与充分性
- **实验数量**：总计超过10组主实验，包括：
  - 注意力分布统计分析（3个数据集，多种测试）
  - 结构扰动实验（4个数据集 × 5种扰动，并用3种基座模型验证）
  - 注意力适应性可视化（多数据集，区分令牌类型）
  - 注意力窗口对比实验（4个数据集 × 至少8种k设置）
  - 跨视角迁移矩阵实验（4个数据集，训练 - 测试组合）
  - 模型/模板消融：更换基座模型、设计4种不同指令模板进行验证。
- **充分性**：实验设计系统，从“是否理解结构”到“如何关注结构”再到“如何改进视角”，逻辑严密。通过多数据集、多模型、统计检验、可视化、消融等方式确保了发现的稳健性。比较对象明确，设置公平，支撑了结论。

### 6. 论文的主要结论与发现
- **LLM能识别图数据但几乎不利用连接信息**：微调后节点注意力分布发生显著变化，但随机打乱图连接对性能影响甚微（除Roman - Empire外）。LLM更多依赖文本 - 节点交互，而非节点间关系。
- **注意力分布不适应图拓扑**：因位置偏差，节点 - 节点注意力呈U形或斜线形，与理想中的中心节点优先模式不符。文本 - 节点注意力更合理，说明LLM在图数据上的瓶颈在于节点间关系建模。
- **发现两种典型注意力畸变**：
  - 常规**Attention Sink**：某些固定位置获得异常高注意力。
  - 独特**Skewed Line Sink**：注意力热图中出现偏离主对角线的亮带，可能捕捉到非预期的空间依赖。
- **最优注意力窗口介于全连接和固定连接之间**：含有部分拓扑信息的中间窗口（k=2,3）训练性能最佳，且具有“小视角训练→大视角推理”的迁移能力，可直接应用于标准LLM推理，无需修改掩码。

### 7. 优点
- **视角新颖**：首次从注意力机制内部对LLM处理图数据进行系统性实证研究，填补了理解空白。
- **方法严谨**：结合了统计检验、受控扰动实验、消除位置偏见的技巧以及可定制的注意力窗口，分析维度全面。
- **发现具体且有启发性**：识别出“Skewed Line Sink”等独特现象，并提炼出“小窗口训练、大窗口推理”的实用策略，为后续改进提供了明确靶点。
- **实验充分**：覆盖同配和异配多种数据集，验证了多种基座模型和指令模板，结果置信度较高。

### 8. 不足与局限
- **模型与架构受限**：主要基于7B规模的LLaMA系列模型，结论能否扩展到更大模型（如70B）或非自回归架构尚不明确。
- **图输入范式单一**：仅沿用了LLaGA的固定模板和采样方案，未探索其他图序列化方法下的注意力行为。
- **分析覆盖不完整**：作者坦言由于篇幅和资源限制，只分析了部分现象，仍有大量注意力行为（如层间差异、头间差异）未深入挖掘。
- **应用转化距离**：研究集中在现象发现和训练策略，尚未将观察结果直接固化为新的模型架构或损失函数来系统性地提升图任务性能。
- **个别数据集异常**：Roman - Empire数据集表现出理想的“扰动 - 退化”趋势，但其他数据集不显著，这一差异的根本原因未被完全厘清，可能隐含数据特异性风险。

（完）
