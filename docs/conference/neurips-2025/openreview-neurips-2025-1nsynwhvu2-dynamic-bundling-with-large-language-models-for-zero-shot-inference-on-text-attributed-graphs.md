---
title: Dynamic Bundling with Large Language Models for Zero-Shot Inference on Text-Attributed Graphs
title_zh: 动态捆绑与大型语言模型用于文本属性图的零样本推理
authors: "Yusheng Zhao, Qixin Zhang, Xiao Luo, Weizhi Zhang, Zhiping Xiao, Wei Ju, Philip S. Yu, Ming Zhang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=1nSynwHvu2"
tags: ["query:graph-llm"]
score: 8.0
evidence: LLM通过动态文本捆绑对文本属性图进行零样本推理
tldr: LLM在文本属性图上直接推理面临图结构信息缺失和回答不可靠的挑战。本文提出DENSE方法，将关联文本动态捆绑后查询LLM获得捆绑级标签，再用这些标签监督图学习，从而缓解LLM幻觉并注入拓扑信息。实验表明DENSE在零样本节点分类等多个任务上显著提升准确率。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-1nsynwhvu2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1458, \"height\": 642, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1nsynwhvu2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1424, \"height\": 365, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1nsynwhvu2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1445, \"height\": 359, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-1nsynwhvu2/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1439, \"height\": 609, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1nsynwhvu2/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 711, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1nsynwhvu2/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 707, \"height\": 319, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1nsynwhvu2/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1437, \"height\": 205, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1nsynwhvu2/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1442, \"height\": 403, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1nsynwhvu2/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1438, \"height\": 107, \"label\": \"Table\"}]"
motivation: LLM在文本属性图上孤立使用文本，缺乏图结构信息且易产生幻觉。
method: 提出动态文本捆绑监督（DENSE），通过文本捆绑查询LLM得到标签以监督图模型。
result: 在零样本节点分类等任务上准确率明显提升。
conclusion: DENSE为LLM在图数据上的可靠推理提供了新思路。
---

## Abstract
Large language models (LLMs) have been used in many zero-shot learning problems, with their strong generalization ability. Recently, adopting LLMs in text-attributed graphs (TAGs) has drawn increasing attention. However, the adoption of LLMs faces two major challenges: limited information on graph structure and unreliable responses. LLMs struggle with text attributes isolated from the graph topology. Worse still, they yield unreliable predictions due to both information insufficiency and the inherent weakness of LLMs (e.g., hallucination). Towards this end, this paper proposes a novel method named Dynamic Text Bundling Supervision (DENSE) that queries LLMs with bundles of texts to obtain bundle-level labels and uses these labels to supervise graph neural networks. Specifically, we sample a set of bundles, each containing a set of nodes with corresponding texts of close proximity. We then query LLMs with the bundled texts to obtain the label of each bundle. Subsequently, the bundle labels are used to supervise the optimization of graph neural networks, and the bundles are further refined to exclude noisy items. To justify our design, we also provide theoretical analysis of the proposed method. Extensive experiments across ten datasets validate the effectiveness of the proposed method.

---

## 论文详细总结（自动生成）

# 论文总结：动态捆绑与大型语言模型用于文本属性图的零样本推理

## 1. 论文的核心问题与整体含义
- **研究背景**：文本属性图（TAG）广泛存在于引文网络、社交网络等场景，标注成本高昂，因此零样本推理显得尤为重要。大型语言模型（LLM）具备强大的零样本泛化能力，已被尝试引入TAG任务。
- **核心挑战**：
  - **图结构信息有限**：LLM难以天然地理解非欧氏空间的图拓扑，将拓扑转化为文本序列会带来信息损失。
  - **回答不可靠**：LLM自身的幻觉问题，加之输入信息不足，容易产生错误伪标签，进而污染下游的图学习（如监督GNN）。
- **整体含义**：本文提出一种名为**DENSE（Dynamic Text Bundling Supervision）** 的方法，通过将拓扑或语义上相近的节点文本**动态捆绑**后查询LLM，获取更可靠的捆绑级标签，并以此监督图神经网络，从而在零样本条件下显著提升节点分类性能。

## 2. 论文提出的方法论
### 2.1 核心思想
不再对单个节点进行LLM查询和伪标签生成，而是将一组关联节点的文本**打包**成一个“文本束”，让LLM判断该束中的**主要类别**（模式类别），再用这个束级标签来训练GNN，并从理论层面证明其对束内“异常节点”更具容忍度。

### 2.2 关键技术细节
1. **捆绑采样**
   - 对同配图（高 homophily）：基于拓扑邻近性，从核心节点的 $k$-hop 邻居中选取节点构成束（$k$ 自适应调整，直到束大小 $n_B$ 满足）。
   - 对异配图（低 homophily）：基于语义邻近性，利用节点嵌入的欧氏距离选取最相似的 $n_B$ 个节点。
2. **捆绑查询**
   - 构建提示模板：将束内所有节点的文本属性拼接，附加数据集描述与任务描述，要求LLM输出该束中**大多数文本**所属的类别。
3. **捆绑监督**
   - 设计两种损失函数训练GNN：
     - 熵基损失：将束内节点logits平均后做softmax得到束类别分布，再与LLM给出的束标签计算交叉熵。
     - 排序基损失：当束标签对应的类别在束分布中不是最高概率值时进行惩罚，侧重于束标签在束内的“支配性”。
   - 最终训练损失为二者之和。
4. **捆绑精炼**
   - 在训练过程中，依据节点对束标签类别的置信度，动态剔除置信度最低的节点，降低噪声对监督的影响。
5. **理论分析**
   - 定理3.1：证明束级监督相比个体级监督，对不与束标签一致的异常节点施加的梯度惩罚更小，即更鲁棒。
   - 定理3.2：在GNN一阶、二阶导数有界的条件下，导出熵基损失函数的平滑性。
   - 定理3.3：在满足一定条件时，梯度下降法可使模型参数收敛到总损失的一个稳定点。

### 2.3 算法流程（文字描述）
- 输入文本属性图 $\mathcal{G} = \langle \mathcal{V}, \mathcal{E}, \mathcal{T} \rangle$，束大小 $n_B$，束数量 $n_S$，精炼轮次 $\mathcal{R}$，总训练轮次 $T$。
- 对 $i=1,\dots,n_S$：
  - 采样核心节点，根据图的同配性质选择邻近节点组成束；
  - 拼接束内文本属性，构造提示并查询LLM，获得束标签。
- 迭代训练GNN $T$ 轮：
  - 计算熵基损失和排序基损失；
  - 若当前轮次属于 $\mathcal{R}$，则对每个束剔除对束标签置信度最低的节点。
- 用训练好的GNN预测所有节点的类别。

## 3. 实验设计
- **数据集（10个）**：
  - 引文网络：Cora, CiteSeer
  - 知识图谱：WikiCS
  - 电商网络：History, Children, Sportsfit
  - 大学网页网络：Cornell, Texas, Wisconsin, Washington
  - 涵盖高同配图（前6个）与低同配图（后4个），覆盖多领域。
- **对比方法（15种）**：
  - 纯文本编码器：SBERT、RoBERTa、TE-3-Large、LLM2Vec
  - 生成式LLM：GPT-3.5-turbo、GPT-4o
  - 图自监督学习：DGI、GraphMAE
  - 图基础模型/LLM+图方法：OFA、GOFA、UniGLM、ZeroG、GraphGPT、LLAGA、LLM-BP
- **实现细节**：默认LLM为GPT-4o，束大小 $n_B=5$，束数 $n_S=100$，同配图用GCN，异配图用GloGNN，训练500轮，精炼在第300和第400轮执行。

## 4. 资源与算力
- **GPU**：1块NVIDIA RTX 3090 (24GB显存）。
- **训练时长**：论文给出了GNN训练时间（例如Cora 11秒，Sportsfit 258秒），但**未提供查询LLM所消耗的API费用或时间**，仅说明该部分依赖于网络状况。

## 5. 实验数量与充分性
- **主实验**：10个数据集 × 15个基线，提供了全面的性能对比表。
- **消融实验**：在4个数据集上测试了6种变体（随机采样、个体查询、去除熵损失/排序损失、个体监督、无精炼），系统性验证各组件贡献。
- **超参数分析**：研究了束大小 $n_B$ 和束数量 $n_S$ 对精度的影响，并给出图形展示。
- **LLM鲁棒性测试**：对比了GPT-4o、GPT-3.5-turbo、GPT-4.1-nano、Deepseek-V3、Gemini-2.5-flash共5种LLM在4个数据集上的表现。
- **LLM查询能力分析**：对比了LLM在“束查询”与“个体查询”下的分类准确率，并关联最终方法性能。
- **理论分析**：提供了3个定理及其证明，从数学上支撑方法设计。
总体而言，实验在数据集、基线、消融、参数敏感性、LLM选择等维度均做了充分验证，实验设计客观、公平，且开源了代码。

## 6. 论文的主要结论与发现
- DENSE在所有10个数据集上均优于15种基线方法，证明动态文本捆绑能有效提升零样本节点分类性能。
- 捆绑查询LLM比单独查询每个节点更可靠，且捆绑监督对束内噪声节点具有更强的容忍能力。
- 方法对不同LLM主干具有较好的鲁棒性，可随LLM的进步而进一步提升。
- 消融实验证实，邻近采样、捆绑查询、两种损失函数以及动态精炼都对最终效果有显著贡献。

## 7. 优点
- **新颖性**：首次将“文本捆绑”概念引入LLM与图学习的结合，巧妙缓解了LLM在图任务中的信息不足和幻觉问题。
- **理论深度**：提供了关于异常节点容忍度、损失平滑性以及收敛性的严格理论分析，增强了方法的可解释性与可信度。
- **灵活性与通用性**：可适配不同类型图（同配/异配）和多种GNN架构，也能兼容不同LLM。
- **实验完备**：涵盖多领域数据集、大量基线、详尽的消融和超参数研究，并开放源代码，便于复现。

## 8. 不足与局限
- **依赖图同配性判断**：采样策略需预判图是同配还是异配，实践中可能需要额外步骤（如调用LLM估计），论文虽给出建议但未完全自动化。
- **查询成本**：每个束需查询LLM一次（默认100次），对大规模图或使用昂贵API时成本较高，论文仅在捆绑数量上进行简单权衡，未深入探讨成本与性能的帕累托最优。
- **实验覆盖**：未报告多次实验的标准差或显著性检验，结果的统计稳健性未完全展示。
- **适用范围限制**：仅适用于节点具备LLM可理解的文本属性的图，对于非文本属性图需额外转换，且当GNN在特定图结构上表现较差时，方法效果也会受限。
- **极端场景**：未详细分析在类别数极大或极度异配图上捆绑采样策略的失效风险。

（完）
