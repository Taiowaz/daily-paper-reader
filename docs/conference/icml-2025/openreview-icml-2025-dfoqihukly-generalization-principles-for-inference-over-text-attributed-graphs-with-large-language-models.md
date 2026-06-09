---
title: Generalization Principles for Inference over Text-Attributed Graphs  with Large Language Models
title_zh: 基于大语言模型的文本属性图推理泛化原则
authors: "Haoyu Peter Wang, Shikun Liu, Rongzhe Wei, Pan Li"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=dfOqiHuklY"
tags: ["query:graph-llm"]
score: 10.0
evidence: 大语言模型用于文本属性图推理
tldr: 在大语言模型（LLM）与图学习的交叉研究中，文本属性图推理面临两大核心挑战：LLM有限的上下文长度难以处理大规模节点邻域，以及节点嵌入与LLM token空间存在不对齐。本文提出LLM-BP框架，通过两个原则确保泛化：使用LLM编码器和任务感知提示实现任务自适应嵌入，统一属性空间；并设计信念传播式迭代以汇聚邻域信息，缓解上下文限制。与仅使用图神经网络或LLM的传统方法相比，LLM-BP在多个文本属性图基准的节点分类和链接预测任务上均展现出显著的零样本性能提升，验证了原则的有效性。该框架为LLM与图结构数据的深度整合提供了坚实的理论依据和实用方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-dfoqihukly/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1746, \"height\": 547, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dfoqihukly/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 808, \"height\": 643, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dfoqihukly/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 787, \"height\": 743, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dfoqihukly/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 825, \"height\": 333, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dfoqihukly/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 813, \"height\": 321, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dfoqihukly/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1588, \"height\": 453, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dfoqihukly/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1701, \"height\": 358, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-dfoqihukly/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 837, \"height\": 423, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dfoqihukly/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1772, \"height\": 688, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dfoqihukly/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1030, \"height\": 629, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dfoqihukly/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1777, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dfoqihukly/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1779, \"height\": 306, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dfoqihukly/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 906, \"height\": 825, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dfoqihukly/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1783, \"height\": 321, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dfoqihukly/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 915, \"height\": 290, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dfoqihukly/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 905, \"height\": 206, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dfoqihukly/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1781, \"height\": 1089, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dfoqihukly/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1777, \"height\": 420, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dfoqihukly/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1064, \"height\": 495, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dfoqihukly/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 898, \"height\": 495, \"label\": \"Table\"}]"
motivation: 图标注数据稀缺，LLM用于图推理时面临上下文长度与嵌入空间对齐的双重挑战。
method: 提出LLM-BP框架，通过任务自适应嵌入和LLM编码器与提示统一属性空间，结合信念传播迭代聚合邻域信息。
result: 在多个文本属性图基准上，LLM-BP实现了显著的零样本节点分类和链接预测性能提升。
conclusion: 验证了所提泛化原则的有效性，为LLM与图结构的深度融合提供了理论指导与实用框架。
---

## Abstract
Large language models (LLMs) have recently been introduced to graph learning, aiming to extend their zero-shot generalization success to tasks where labeled graph data is scarce. Among these applications, inference over text-attributed graphs (TAGs) presents unique challenges: existing methods struggle with LLMs' limited context length for processing large node neighborhoods and the misalignment between node embeddings and the LLM token space. To address these issues, we establish two key principles for ensuring generalization and derive the framework LLM-BP accordingly: (1) **Unifying the attribute space with task-adaptive embeddings**, where we leverage LLM-based encoders and task-aware prompting to enhance generalization of the text attribute embeddings; (2) **Developing a generalizable graph information aggregation mechanism**, for which we adopt belief propagation with LLM-estimated parameters that adapt across graphs. Evaluations on 11 real-world TAG benchmarks demonstrate that LLM-BP significantly outperforms existing approaches, achieving 8.10\% improvement with task-conditional embeddings and an additional 1.71\% gain from adaptive aggregation. The code and task-adaptive embeddings are publicly available.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义
- **核心问题**：将大语言模型（LLM）应用于文本属性图（TAG）推理时，面临两大挑战：
  - LLM的上下文长度有限，无法处理大规模节点邻域。
  - 图嵌入与LLM token空间存在语义不对齐，导致零样本泛化困难。
- **研究动机**：图标注数据稀缺，亟需能在未见过的图上进行零样本节点分类的通用方法。本文旨在从第一性原理出发，建立可靠的泛化原则。
- **整体含义**：提出一种免训练、由原则驱动的框架 **LLM‑BP**，通过**任务自适应嵌入**统一文本空间，并用类信念传播的机制实现可泛化的图信息聚合，从而跨越文本域和网络结构的分布偏移。

### 2. 方法论
#### 2.1 原则一：统一文本空间，获取任务自适应嵌入
- 使用基于解码器‑编码器结构的 **LLM2Vec** 生成节点嵌入，而非小型的双向语言模型。
- 设计**任务条件提示模板**：`<Instruct> {任务描述} {类别信息} <query> 节点原始文本 <response>`。
- 将 LLM 在 \<response\> 位置的输出隐状态作为该节点的任务自适应嵌入 \(h^{X}\)。
- 在零样本设定下，随机采样少量节点，用 GPT‑4o 推断其标签并聚类，以聚类中心的平均嵌入作为类嵌入 \(q^C\)；少样本下直接用已标记节点的平均嵌入。

#### 2.2 原则二：可泛化的自适应图聚合机制（信念传播）
- 将图建模为**马尔可夫随机场（MRF）**，节点标签为随机变量，节点势 \(\varphi_{y_i}(X_i)\) 由任务嵌入与类嵌入的余弦相似度估计；边势 \(\psi_{ij}(y_i,y_j)\) 刻画相邻节点标签的耦合。
- **边势参数估计**：随机采样少量边对，由 LLM（如 GPT‑4o‑mini）判断是否属于同类，统计“是”的比例得到同配率 \(r\)，进而设置
  \[
  \psi_{ij}(y_i, y_j) = \begin{cases} r, & y_i = y_j \\ 1-r, & y_i \neq y_j \end{cases}
  \]
- **推理算法**：采用 loopy belief propagation（LBP）迭代更新节点信念，公式为
  \[
  \log m^{(k)}_{j\to i}(y_i) \doteq \text{LSE}_{y_j}\bigl[\log\psi_{ij}(y_i,y_j) + \log p^{(k-1)}_j(y_j) - \log m^{(k-1)}_{i\to j}(y_j)\bigr]
  \]
  \[
  \log p^{(k)}_i(y_i) \doteq \log p^{(0)}_i(y_i) + \sum_{j\in\mathcal{N}(i)} \log m^{(k)}_{j\to i}(y_i)
  \]
  其中 LSE 为 log‑sum‑exp。
- **线性近似（BP appr.）**：当文本质量有限时，单次线性传播：
  \[
  \log p^{(1)}_i(y_i) \doteq \log p^{(0)}_i(y_i) + \operatorname{sgn}\!\left(\log\frac{r}{1-r}\right) \sum_{j\in\mathcal{N}(i)} \log p^{(0)}_j(y_i)
  \]
- 最终节点类别由 \(\arg\max_{y_i} p^{(k)}_i(y_i)\) 确定。

#### 2.3 整体流程
1. 用任务自适应编码器获得 \(h^X\)。
2. 零样本时用 LLM 辅助采样并计算类嵌入 \(q^C\)；少样本时直接平均标签嵌入。
3. 用 LLM 估计同配率 \(r\)，初始化节点势 \(p^{(0)}\)。
4. 运行 LBP 或线性近似，输出预测标签。

### 3. 实验设计
- **数据集**：11 个真实世界 TAG 基准，覆盖：
  - 引文网络：Cora, Citeseer, Pubmed（同配）
  - 电商图书：History, Children, Sportsfit（同配）
  - 知识图谱：Wikics（同配）
  - 学校网页：Cornell, Texas, Wisconsin, Washington（异配）
- **基准方法**：
  - 纯编码器：SBert, RoBERTa, text‑embedding‑3‑large, LLM2Vec
  - 纯LLM：GPT‑3.5‑turbo, GPT‑4o（直接读原始文本）
  - 微调编码器/GNN：ZeroG, UniGLM, DGI, GraphMAE
  - LLM+图适配器：LLaGA, GraphGPT, TEA‑GLM
  - 多任务图基础模型：OFA, GOFA
  - 数据增强LLM：LLM‑GNN
  - 邻域平均聚合：NA
- **评估场景**：零样本节点分类（全节点测试）、k‑shot 节点分类（k=1,3,5,10）、零样本链接预测。
- **公平性**：所有需要训练的基线均在 ogbn‑arxiv 上预训练/微调，与 LLM‑BP 零‑shot 对比；LLM‑BP 无训练。

### 4. 资源与算力
- 本地实验服务器：AMD EPYC 7763 64‑Core CPU，8× NVIDIA RTX 6000 Ada GPU。
- 主要实现框架：PyTorch, PyG, Huggingface Transformers。
- **训练开销**：LLM‑BP 完全免训练，不需要微调 LLM 或 GNN。主要计算在节点嵌入生成和少步信念传播上。
- **API 调用**：使用 GPT‑4o 或 GPT‑4o‑mini 估计同配率 \(r\)（每个数据集仅需约 100 对边）和零样本标签推断，API 成本较低但文中未精确报告费用。
- **训练时长**：未明确说明，基线方法的训练时长也未提及。

### 5. 实验数量与充分性
- **实验组数量**：
  - 零样本主实验：11 个数据集 × 约 15 种方法，报告 Accuracy 和 Macro‑F1，附带平均排名。
  - 消融实验：
    - 不同编码器的任务自适应效果（t‑SNE 可视化、显著性检验）。
    - LLM 估计同配率 \(r\) 的准确度（4 种 LLM，不同采样边数）。
    - BP vs. BP appr. vs. Raw vs. NA 的组合效应。
    - 任务自适应编码对 SBert/RoBERTa/text‑embedding‑3‑large 的影响。
    - 与 LLM‑GNN、TEA‑GLM 的额外对比。
  - 少样本实验：4 种 k 值，10 次随机采样，报告 Accuracy ± 标准差。
  - 链接预测实验：部分数据集上的零样本性能。
- **统计检验**：针对任务自适应编码的改进进行了配对 t 检验或 Wilcoxon 检验，并给出置信区间，证明提升显著。
- **公平性**：同配/异配图分别对比，基线覆盖主流思想，预训练数据对齐，评估指标统一，实验设计充分且客观。

### 6. 主要结论与发现
- **任务自适应嵌入**带来平均 8.10% 的 Accuracy 提升（相对于最佳 LM 编码器）。
- **BP 聚合**在此基础上再提升 1.71%，且在异配图上依然有效，普通邻域平均（NA）在异配图上会退化。
- LLM‑BP 和 LLM‑BP (appr.) 在零样本节点分类中取得**最高的平均排名**，在少样本下同样稳健。
- 现有“将图嵌入对齐到 LLM token 空间”的方法（如 LLaGA, GraphGPT）性能弱于简单的 SBert 编码器，说明其泛化性主要来自于基础 LM 而非 LLM 的推理，该类方法需谨慎。
- LLM 作为“图分析代理”可以较准确地估出图的同配性，为 BP 提供关键参数。

### 7. 优点
- **原则驱动**：从 MRF 和信念传播的数学基础出发，可解释性强。
- **完全免训练**：不需要任何微调，纯推理流程。
- **自适应性强**：同时适应文本域漂移和图结构漂移（同配/异配）。
- **LLM 应用创新**：不将 LLM 当作黑盒接收压缩后的嵌入，而是让其承担编码和图分析两个角色。
- **实验全面扎实**：覆盖 11 种数据集、多种基线、零/少样本设定、统计检验和可视化，结论可信度高。
- **工程友好**：类嵌入生成、BP 迭代均简单高效。

### 8. 不足与局限
- **LLM 依赖**：同配性估计和零样本标签推断依赖强 LLM（如 GPT‑4o），小模型（Mistral 7B）会失败，无法完全在本地离线部署。
- **链接预测任务未深入优化**：任务自适应提示未针对链接预测设计，性能提升有限。
- **边势建模简化**：仅用一个全局同配率 \(r\)，未估计类别间的转移概率，可能丢失精细的结构信息。
- **并非全任务图基础模型**：目前限于属性推理，不能直接处理结构推理、图生成等任务。
- **采样成本**：即使采样少量节点和边，仍需调用 LLM，可能带来推理时间和费用。
- **编码器选择**：仅实验了 LLM2Vec（Mistral‑7B），未探索不同 LLM 编码器的影响。

（完）
