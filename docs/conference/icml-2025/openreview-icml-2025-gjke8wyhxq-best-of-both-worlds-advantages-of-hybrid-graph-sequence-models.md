---
title: "Best of Both Worlds: Advantages of Hybrid Graph Sequence Models"
title_zh: 两全其美：混合图序列模型的优势
authors: "Ali Behrouz, Ali Parviz, Mahdi Karami, Clayton Sanford, Bryan Perozzi, Vahab Mirrokni"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=GJKe8WYHxq"
tags: ["query:graph-llm"]
score: 6.0
evidence: 提出将序列模型应用于图数据的框架，实现图表示学习与序列模型的结合。
tldr: 针对图数据缺乏统一序列建模理论的问题，提出图序列模型（GSM）框架，将Transformer和线性RNN等序列模型统一应用于图结构数据，并分析混合架构的数学特性。实验表明，混合消息传递与序列模型的架构在多个图任务上性能最优，为图表示学习与语言模型骨干的结合提供了理论支撑和实用方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-gjke8wyhxq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1690, \"height\": 644, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gjke8wyhxq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 796, \"height\": 433, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gjke8wyhxq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1609, \"height\": 595, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gjke8wyhxq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 540, \"height\": 367, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-gjke8wyhxq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 909, \"height\": 981, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gjke8wyhxq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 788, \"height\": 1038, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gjke8wyhxq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1063, \"height\": 797, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gjke8wyhxq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 680, \"height\": 686, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gjke8wyhxq/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 872, \"height\": 682, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gjke8wyhxq/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 854, \"height\": 813, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gjke8wyhxq/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1415, \"height\": 1314, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gjke8wyhxq/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1588, \"height\": 1007, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gjke8wyhxq/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1767, \"height\": 491, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gjke8wyhxq/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1149, \"height\": 213, \"label\": \"Table\"}]"
motivation: 图学习领域缺乏对序列模型应用于图数据的统一理论框架。
method: 提出图序列模型GSM，统一描述Transformer和线性RNN等序列模型在图上的应用，并分析混合架构优劣。
result: 实验表明混合消息传递与序列模型的架构在多个图任务上取得最优性能。
conclusion: 混合图序列模型兼具消息传递和序列建模优势，为图表示学习与序列模型结合提供了新方向。
---

## Abstract
Modern sequence models (e.g., Transformers and linear RNNs) emerged as dominant backbones of recent deep learning frameworks, mainly due to their efficiency, representational power, and/or ability to capture long-range dependencies. Recently, adopting these sequence models for graph-structured data has gained popularity as the alternative to Message Passing Neural Networks (MPNNs). There is, however, a lack of a common foundation about what constitutes a good graph sequence model, and a mathematical description of the benefits and deficiencies in adopting different sequence models for learning on graphs. To this end, we introduce the Graph Sequence Model (GSM), a unifying framework for applying sequence models to graph data.  The GSM framework allows us to understand, evaluate, and compare the power of different sequence model backbones in graph tasks. Building on this insight, we propose GSM++, a fast hybrid model that hierarchically tokenizes the graph using Hierarchical Affinity Clustering (HAC) and then encodes these sequences via a hybrid architecture. The  theoretical and experimental findings confirm that GSM++ outperforms baseline models on most benchmarks.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义
- **研究动机**：现代序列模型（Transformers、线性RNN/SSM 等）在文本、视觉等任务上取得巨大成功，并被越来越多地迁移到图数据上，试图替代传统的消息传递神经网络（MPNNs）。然而，**缺乏一个统一的框架来形式化描述“什么是好的图序列模型”**，不同序列模型在图上的优缺点没有系统的数学刻画。
- **核心问题**：如何从理论上理解序列模型在图任务中的能力差异？如何在统一框架下比较不同 tokenization 与序列编码器的组合？进而，能否设计出兼具两类模型优点的混合图序列模型？
- **整体含义**：该工作提出 **Graph Sequence Model (GSM)** 框架，把图到序列的转换过程抽象为“Tokenization → Local Encoding → Global Encoding”三个阶段，为系统评估和设计图序列模型奠定基础。在此基础上，进一步提出 **GSM++**，利用层次亲和聚类（HAC）进行层次化 tokenization，并用 **SSM + Transformer** 的混合编码器以及 **混合 tokenization（MoT）** 来平衡不同任务的需求。

## 2. 方法论
- **GSM 统一框架**：任何图序列模型均可被分解为三个模块：
  1. **Tokenization**：将图转化为一组序列，分为 **节点/边 tokenizer**（直接序列化节点或边，依赖位置/结构编码）和 **子图 tokenizer**（如 k-hop 邻域、随机游走等）。
  2. **Local Encoding**：使用局部模型（通常为 MPNN）对每个 token 对应的子图进行编码，注入局部归纳偏置。
  3. **Global Encoding**：利用序列模型（如 Transformer、Mamba、S4、xLSTM 等）在 token 序列上捕获长程依赖。
- **理论分析**（指导模型设计）：
  - **计数任务**：因果循环模型（如 SSM）天然能完成颜色计数，而非因果 Transformer 若无合适的位置编码则无法计数（定理 1）。
  - **节点有序性与灵敏度**：SSM 的灵敏度随 token 距离增加而下降，因此**将相似节点放在一起**有利于信息交互；但 SSM 在深层仍会出现表征塌缩（定理 2 及推论）。Transformer 虽然恒灵敏度，但不会因层数加深而忽略长程信息。这启发混合架构。
  - **连通性任务**：Transformer 在一般情况更高效，但若序列具有**节点局部性**（Node Locality），则循环模型用极少的参数即可解决连通性（定理 4, 5）。
- **GSM++ 的设计**：
  - **层次亲和聚类 Tokenization（HAC）**：基于 Boruvka 算法构建层次聚类树，再通过 **DFS 或 BFS 遍历**得到序列。DFS 路径编码节点在层次中的位置，BFS 则按粒度生成多条序列。HAC 能产生节点相似性顺序，满足局部性条件（定理 6），并带来**层次结构偏置**。
  - **层次位置编码**：利用 HAC 树中不同粒度簇间最短路径，生成多尺度的相对位置编码。
  - **混合序列模型**：采用 **Mamba（SSM）+ Transformer** 的 2 层混合块，SSM 提供距离敏感的归纳偏置，Transformer 避免表征塌缩并保持置换等变性（定理 7 非正式）。
  - **混合 Tokenization（MoT）**：为每个节点通过可学习路由器从多种 tokenizer 中选择 top‑2，拼接后编码，实现自适应的 token 表示。
- **公式与算法流程**（用文字说明）：
  - Tokenization 后得到序列集合 \(\{S^{(i)}\}\)，每个序列再由局部编码器 \(\phi_{\text{Local}}\) 变换为向量序列 \(\tilde{S}^{(i)}\)。
  - 全局编码阶段，使用序列模型 \(\Psi_i\) 和聚合函数 \(\text{AGG}\) 获得最终表示 \(y^{(i)} = \Psi_i(\text{AGG}(\tilde{S}^{(1)}, \dots, \tilde{S}^{(T)}))\)。
  - MoT 中通过线性路由器 \(S = \sigma(XW_r)\) 计算路由分数，取 Top‑2 索引，对相应 tokenization 的输出拼接得到输入序列。

## 3. 实验设计
- **任务与数据集**：
  - **合成/分析任务**：节点度、环检测、三角计数（局部任务）；连通性、颜色计数、最短路径（全局任务），在 1K 和 100K 规模图上评估。
  - **GNN Benchmark**：MNIST、CIFAR10、PATTERN、MalNet‑Tiny。
  - **Long‑Range 图基准**：COCO‑SP、PascalVOC‑SP、Peptides‑Func。
  - **异配图数据集**：Roman‑empire、Amazon‑ratings、Minesweeper。
  - **大规模图**：ogbn‑arxiv、ogbn‑products。
- **对比方法**：
  - MPNNs：GCN、GIN、GAT、Gated‑GCN、GraphSAGE 等。
  - Graph Transformers：GraphGPS、Exphormer、NAGphormer、GRIT、NodeFormer、GOAT 等。
  - 循环基模型：Graph Mamba (GMN)、GRED 等。
- **消融实验**：
  - 在 GraphGPS 和 NAGphormer 框架上逐步加入 Hybrid 编码器、HAC tokenization、MoT。
  - 对 GSM++ 逐步移除层次位置编码、混合编码器、HAC tokenization，观测性能变化。
  - 大规模序列模型 × tokenization 组合评估：9 种序列编码器 × 6 种 tokenizer × 7 个数据集，共 378 组实验，以归一化排名展示。

## 4. 资源与算力
- 论文**未明确报告**所用 GPU 型号、数量及训练时长等具体算力信息。
- 仅在大型图实验中给出了训练时间和显存占用（如 ogbn‑arxiv 上 GSM++ BFS 占用 24.8 GB，训练 2.33 s/epoch），但未说明硬件环境。

## 5. 实验数量与充分性
- 实验组数非常庞大：9×6×7 组合实验、多个基准数据集对比、详尽消融、效率分析等，覆盖从合成任务到大规模真实数据。
- 对比基线既包括传统 MPNNs，也涵盖多种先进的 Transformer 和 SSM 模型，**比较全面且公平**。
- 消融实验系统地验证了 HAC tokenization、混合编码器、层次 PE 的各自贡献。
- 评估指标根据任务性质选择 Accuracy、F1 score、RMSE、ROC AUC、AP 等，合理可靠。

## 6. 主要结论与发现
- **不存在一种在所有图任务上绝对最优的序列模型或 tokenization 方法**，支持“没有免费午餐”观点，实际建模需根据任务特性选择。
- **Transformer 在全局任务（如连通性）上具有参数效率优势**，但其置换等变性使其难以处理需要顺序归纳偏置的任务（如计数）。
- **SSM/RNN 在具备良好节点排序时极为高效**，HAC tokenization 能够提供这种“利于局部性”的顺序，使循环模型在连通性上仅需常数级隐藏状态。
- **混合模型（SSM + Transformer）融合了两类模型优点**：SSM 引入距离敏感偏置，Transformer 防止表征塌缩并保留置换等变性，在多数任务中取得一致提升。
- **GSM++ 在 10 个基准中 8 个达到最优**，且在大规模图上兼具效率和性能，验证了 HAC tokenization、混合编码器和 MoT 的有效性。

## 7. 优点
- **统一框架**：GSM 将现有多种图序列模型纳入统一视角，便于系统对比和理论分析。
- **理论深度**：结合图算法任务（计数、连通性、最短路径等）给出了不同序列模型与 tokenization 优劣的严格数学表述。
- **创新设计**：HAC tokenization 同时提供层次结构和自然排序，混搭 Mamba + Transformer 的思路巧妙，MoT 引入自适应 tokenization 选择。
- **实验充分**：从理论分析到大规模实证，覆盖多种序列模型和数据集，结果稳健，具有说服力。
- **可复现性**：文中提供了详细的模型结构和算法描述，且在公开基准上评估，利于后续复现。

## 8. 不足与局限
- **无免费午餐证实**：结论本身也说明 GSM++ 并非在所有场景的最优解，仍需根据任务选择合适的组件，自动选择机制（MoT）可能引入额外开销。
- **理论混合优势实例较特殊**：混合模型优于纯模型的证明基于人为构造的 factored graph，在一般真实图中的混合优势仍需更多理论支撑。
- **算力细节缺失**：未说明 GPU 配置、批次大小等，使得读者难以精确评估资源需求。
- **大规模图实验范围有限**：虽在 ogbn 上进行了评估，但更具挑战的亿级图实验因显存或时间限制未能深入（部分模型 OOM）。
- **HAC 预处理**：虽然时间复杂度可较低，但在动态图或在线场景下重新计算 HAC 树的开销仍需审视。

（完）
