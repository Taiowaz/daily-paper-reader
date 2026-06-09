---
title: "Flatten Graphs as Sequences: Transformers are Scalable Graph Generators"
title_zh: 展平图为序列：Transformer 作为可扩展的图生成器
authors: "Dexiong Chen, Markus Krimmel, Karsten Borgwardt"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=eszmES7j1F"
tags: ["query:graph-llm"]
score: 7.0
evidence: 利用类LLM架构的自回归变换器通过展平图为序列进行图生成
tldr: AutoGraph 提出了一种将属性图展平为随机令牌序列的可逆过程，使仅解码器变换器能以自回归方式生成图，采样复杂度与边数线性相关。该方法在图生成任务上达到最优性能，并将图序列前缀与语言建模中的子句建立直接联系，为使用变换器处理图结构化数据提供了可扩展的新思路。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-eszmes7j1f/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1444, \"height\": 370, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eszmes7j1f/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1441, \"height\": 291, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eszmes7j1f/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1170, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eszmes7j1f/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1445, \"height\": 840, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eszmes7j1f/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1450, \"height\": 824, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eszmes7j1f/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1452, \"height\": 843, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eszmes7j1f/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1447, \"height\": 932, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eszmes7j1f/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 741, \"height\": 557, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eszmes7j1f/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 815, \"height\": 819, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eszmes7j1f/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 799, \"height\": 821, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eszmes7j1f/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 829, \"height\": 828, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eszmes7j1f/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 833, \"height\": 835, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eszmes7j1f/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1158, \"height\": 691, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eszmes7j1f/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1439, \"height\": 867, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eszmes7j1f/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1440, \"height\": 793, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eszmes7j1f/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1405, \"height\": 1405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eszmes7j1f/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 821, \"height\": 821, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eszmes7j1f/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 825, \"height\": 806, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eszmes7j1f/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 834, \"height\": 823, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eszmes7j1f/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 827, \"height\": 822, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-eszmes7j1f/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1443, \"height\": 488, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eszmes7j1f/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1306, \"height\": 507, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eszmes7j1f/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 730, \"height\": 186, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eszmes7j1f/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1433, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eszmes7j1f/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 874, \"height\": 194, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eszmes7j1f/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 584, \"height\": 163, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eszmes7j1f/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 865, \"height\": 158, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eszmes7j1f/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1438, \"height\": 520, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eszmes7j1f/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1451, \"height\": 878, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eszmes7j1f/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1189, \"height\": 492, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eszmes7j1f/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1444, \"height\": 444, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eszmes7j1f/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1014, \"height\": 229, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eszmes7j1f/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1436, \"height\": 351, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eszmes7j1f/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1434, \"height\": 185, \"label\": \"Table\"}]"
motivation: 现有基于扩散的图生成方法依赖昂贵的节点特征计算，且难以扩展到大规模图。
method: 通过可逆过程将属性图展平为随机令牌序列，用仅解码器变换器自回归建模，序列前缀即诱导子图。
result: 图生成达到最优性能，且采样和序列长度与边数线性相关，适合大稀疏图。
conclusion: 将图表示为序列并利用变换器的语言建模能力，为可扩展图生成开辟了新范式。
---

## Abstract
We introduce AutoGraph, a scalable autoregressive model for attributed graph generation using decoder-only transformers. By flattening graphs into random sequences of tokens through a reversible process, AutoGraph enables modeling graphs as sequences without relying on additional node features that are expensive to compute, in contrast to diffusion-based approaches. This results in sampling complexity and sequence lengths that scale optimally linearly with the number of edges, making it scalable and efficient for large, sparse graphs. A key success factor of AutoGraph is that its sequence prefixes represent induced subgraphs, creating a direct link to sub-sentences in language modeling. Empirically, AutoGraph achieves state-of-the-art performance on synthetic and molecular benchmarks, with up to 100x faster generation and 3x faster training than leading diffusion models. It also supports substructure-conditioned generation without fine-tuning and shows promising transferability, bridging language modeling and graph generation to lay the groundwork for graph foundation models. Our code is available at https://github.com/BorgwardtLab/AutoGraph.

---

## 论文详细总结（自动生成）

# AutoGraph论文深度分析总结

## 1. 核心问题与研究动机
- **问题背景**：图结构数据生成（如药物分子、蛋白质结构、程序合成）是AI重要方向，但现有方法面临结构性约束、不变性保持、可扩展性等挑战。
- **扩散模型局限**：当前主流扩散模型（如DiGress）需在离散图空间执行去噪过程，必须计算全邻接矩阵，内存复杂度O(n²)；每步还需计算节点谱特征，增加O(n³)开销，导致生成慢、训练慢。
- **自回归模型局限**：之前的自回归方法（GraphRNN, GRAN等）要求专门架构（如RNN），序列表示复杂、非令牌化，无法利用大型语言模型（LLM）的进步，且长距离依赖和全局结构一致性差。
- **核心动机**：将图生成为序列预测问题，通过“图到序列”的无损变换，直接应用标准语言模型，实现线性复杂度图生成，桥接图生成和语言建模。

## 2. 方法论：核心技术
- **基本思想：将图展平为随机令牌序列**
  - 提出**分段欧拉邻域路径（Segmented Eulerian Neighborhood Trail, SENT）**，无损编码图的拓扑结构与属性。
  - 随机路径采样生成覆盖所有边的不分段路径，每条路径包含节点及其已访问邻居集，使序列前缀表示诱导子图。
  - 通过顶点重新索引（按首次出现顺序）保证序列对输入图节点顺序的不变性。
  - 插入特殊令牌（`/`分段、`<`和`>`邻居集）构成机器可读的令牌序列。
- **关键理论保证（Thm 2.14, 2.15）**：
  - 因果且半哈密顿的SENT确保任意前缀的生成图是原图的诱导子图，建立与语言模型中“子句”的直接类比。
  - 充分条件：每个节点的邻域集等于其已访问邻居或为空，可通过随机游走简单实现采样。
- **生成建模**：
  - 使用仅解码器Transformer（如LLaMA、GPT-2）以自回归方式最大化令牌序列的对数似然。
  - 训练目标：标准下个令牌预测。
  - 可扩展至属性图：将节点/边类别或离散化属性按交错方式插入令牌序列。
- **算法流程（Algorithm 1）**：
  1. 随机选取未访问节点作为段起点。
  2. 从当前节点出发，若邻域存在未访问节点，则随机选取下个节点并记录其已访问邻居作为邻域集，继续当前段；若无可达未访问节点，则结束当前段，随机重启新段。
  3. 直到所有节点被访问，输出SENT序列。
  4. 时间和空间复杂度均为O(m)（m为边数），长度正比于边数。

## 3. 实验设计
- **数据集**：
  - 小规模合成图：Planar（200张，64节点）、SBM（200张，平均104节点）。
  - 大规模非属性图：Proteins（587张，最大500节点）、Point Clouds（26张，最大5037节点）。
  - 分子属性图：QM9（10万分子，显式氢）、MOSES（158万）、GuacaMol（111万）。
  - 预训练数据集：自建NetworkX合成图集（约2.5万张，多种图族）、PubChem-10M（分子）。
- **评估基准与指标**：
  - MMD（最大均值差异）：度分布、聚集系数、轨道计数、谱。
  - 综合比率RATIO（生成MMD/训练MMD均值）。
  - VUN（同时有效、独特、新颖）用于合成图。
  - 分子生成特有指标：Validity（有效性）、Uniqueness、Novelty、Filters、FCD、SNN等。
- **对比方法**：GraphRNN, GRAN, SPECTRE, EDGE, GraphGen, BiGG, DiGress, GruM, GEEL, ESGG等扩散与自回归模型。

## 4. 资源与算力
- **硬件**：所有实验均在单一NVIDIA H100 (80GB) GPU上完成，搭配8 CPU和最高48GB系统RAM。
- **训练时间**：
  - Planar数据集：训练时间约6.2小时（AutoGraph），比DiGress快约4.2倍；推理速度约0.01秒/图，加速约284倍。
  - SBM：训练13.8小时（3.5x加速），推理0.14秒/图（93x加速）。
  - 分子生成：MOSES/GuacaMol训练不到1天，DiGress需约一周。
- **模型规模**：统一使用LLaMA-small架构（12层，768隐藏维度，113M参数），固定上下文长度2048，batch size 128或64（大图）。

## 5. 实验数量与充分性
- **主实验**：7个数据集（Planar, SBM, Proteins, Point Clouds, QM9, MOSES, GuacaMol），与9种方法对比。
- **效率对比**：在Planar和SBM上测量训练与推理时间，与DiGress、GRAN、ESGG比较。
- **迁移实验**：预训练于NetworkX或PubChem-10M后微调，展示VUN、MMD提升。
- **条件生成**：子结构条件生成（单/多拷贝/不同分子片段），评估有效性、新颖性。
- **消融研究**：
  - 序列架构比较（GPT-2、Mamba、LLaMA）。
  - Top-k采样影响分析。
  - SET vs SENT效果对比。
  - 模型大小（LLaMA-XS, S, M）影响。
- **统计显著性**：报告多次运行的标准差/误差条（Planar和SBM）。
- **评估公平性**：采用与先前工作完全一致的评估协议、数据划分及外部工具包（MOSES/GuacaMol benchmark）。
实验覆盖充分，对比全面，设计客观。

## 6. 主要结论与发现
- AutoGraph在所有测试数据集上达到或超越SOTA，特别是结构有效性和分布拟合。
- 分子生成任务上首次有自回归图生成模型超越扩散模型，且训练/推理大幅加速（最高100x生成加速）。
- 图到序列的令牌化表示成功建立语言模型与图生成的桥梁，序列前缀为诱导子图，利于长距离依赖建模。
- 具备子结构条件生成能力（无需微调），以及跨数据集的可迁移性。
- 消融验证SENT优于SET，Transformer架构优于Mamba，且Top-k采样可调节生成质量。

## 7. 优点
- **创新性强**：首次将图展平为与语言模型直接兼容的令牌序列，并给出子图诱导的理论保证。
- **高效可扩展**：采样、序列长度、训练/推理复杂度均为O(m)，支持大规模稀疏图。
- **性能优异**：多个基准上取得最优，尤其在VUN和分子有效性上表现突出。
- **灵活性与通用性**：可应用于属性/非属性图，支持条件生成，模型架构可任意替换为最新LLM。
- **开源与可复现**：代码公开，提供详细配置和checkpoint。

## 8. 不足与局限
- **数据集规模有限**：图生成基准显著小于LLM预训练语料，限制了对“基础模型”潜力的验证。
- **分子生成的令牌解码**：未约束解码可能产生语义错误序列，需额外约束机制以保证属性图有效。
- **评估指标的依赖性**：MMD等指标依赖核参数选择且小样本方差大。
- **未处理极稀疏或特殊拓扑**：如高度非连通图、有向图、动态图等未尝试。
- **应用场景仍受限**：尚未验证在程序合成、蛋白质设计等实际下游任务的表现。

（完）
