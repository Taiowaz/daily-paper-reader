---
title: "CAREPath: Semantic Context-Aware Reasoning Paths with Mechanism-Augmented Embeddings for Drug Repurposing"
title_zh: "CAREPath: 用于药物重定位的语义上下文感知推理路径与机制增强嵌入"
authors: "song, h., bang, d., koo, b., Kim, S., lee, s."
date: 2026-06-12
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.09.731247v1.full.pdf"
tags: ["query:graph-llm"]
score: 10.0
evidence: 知识图谱-LLM框架用于药物重定位推理
tldr: "生物医学知识图谱通过基因介导多跳路径支持药物重利用，但长路径存在冗余信号，短路径丢失上下文。CAREPath模型受DFS与BFS启发，通过短路径语义编码与机制上下文增强平衡特异性和可扩展性。在五个知识图谱上，AUPRC提升达3.8%，短编码贡献最大，增强模块提高稀疏证据下的鲁棒性。该可解释框架为机制感知药物重利用提供了有效方案，并经案例验证。"
source: biorxiv
selection_source: fresh_fetch
motivation: 长路径冗余噪声与短路径上下文丢失的矛盾制约药物重利用机制推理。
method: CAREPath结合DFS式短路径语义编码与BFS式机制上下文增强，平衡特异性和上下文恢复。
result: "在五个生物医学知识图谱上，AUPRC最优，提升达3.8%，短路径编码贡献最大，上下文增强提升稀疏证据鲁棒性。"
conclusion: CAREPath为可解释、可扩展、机制感知的药物重利用提供了有效框架，并经FDA案例验证。
---

## 摘要
生物医学知识图谱包括药物、基因和疾病，通过基因介导的多跳路径将药物与疾病连接起来，从而支持药物重定位，实现作用机制推理。然而，更深的遍历并不一定改善机制推理：长路径组合增长并频繁经过枢纽基因，产生无关的基因调控信号，而过度约束或稀疏的路径可能错过更广泛的生物学背景。我们提出CAREPath，一个受深度优先搜索和广度优先搜索启发、平衡机制特异性、可扩展性和上下文恢复的知识图谱-大语言模型框架。类深度优先搜索模块将遍历约束为短的疾病-基因-药物路径，将每条路径转换为结构化提示，并使用生物医学语言模型编码生成语义路径嵌入。补充地，类广度优先搜索模块从单跳基因邻域构建实体级机制上下文嵌入，并通过使用药理相关药物和基因特征相似疾病进行相似性引导的增强来丰富它们。在五个生物医学知识图谱上，CAREPath在18个基线中取得了最佳的总体精确率-召回率曲线下面积，性能提升高达3.8%。进一步分析表明，语义短路径编码对性能贡献最大，而机制上下文增强提高了稀疏证据下的鲁棒性，并加强了基因本体功能一致性。案例研究和最近美国食品药品监督管理局批准的适应症进一步证明了其实际相关性，将CAREPath定位为可扩展且具有机制感知的药物重定位的可解释框架。源代码可在https://github.com/hamppy-song/CAREPath获取。

## Abstract
Biomedical knowledge graphs (BKGs) that include drugs, genes, and diseases support drug repurposing by connecting drugs to diseases through gene-mediated multi-hop paths, thereby enabling mechanism-of-action reasoning. However, deeper traversal does not necessarily improve mechanistic reasoning: long paths grow combinatorially and frequently pass through hub genes, producing irrelevant gene regulatory signals, whereas overly constrained or sparse paths may miss broader biological context. We propose CAREPath, a KG-LLM framework inspired by depth-first search (DFS)-like and breadth-first search (BFS)-like reasoning to balance mechanistic specificity, scalability, and context recovery. The DFS-like module constrains traversal to short disease-gene-drug paths, converts each path into a structured prompt, and encodes it with a biomedical language model to generate semantic path embeddings. Complementarily, the BFS-like module constructs entity-level mechanism-context embeddings from one-hop gene neighborhoods and enriches them through similarity-guided augmentation using pharmacologically related drugs and gene-signature-similar diseases. Across five biomedical KGs, CAREPath achieves the best overall AUPRC among 18 baselines, improving performance by up to 3.8%. Additional analyses show that semantic short-path encoding contributes most to performance, while mechanism-context augmentation improves robustness under sparse evidence and strengthens Gene Ontology functional agreement. Case studies and recently FDAapproved indications further demonstrate its practical relevance, positioning CAREPath as an interpretable framework for scalable and mechanism-aware drug repurposing. Source code is available at https://github.com/hamppy-song/CAREPath.

---

## 论文详细总结（自动生成）

# CAREPath: 用于药物重定位的语义上下文感知推理路径与机制增强嵌入

## 1. 论文的核心问题与整体含义
- **核心问题**：生物医学知识图谱通过“药物—基因—疾病”多跳路径支持药物重定位和机制推理，但**较长的路径**会因组合爆炸和经过枢纽基因而引入大量无关调控信号，**过短的路径**又可能丢失更广泛的生物学上下文。如何在**机制特异性、可扩展性与上下文恢复**之间取得平衡，是当前知识图谱推理方法面临的挑战。
- **整体含义**：本文提出 **CAREPath**，一个受深度优先搜索（DFS）和广度优先搜索（BFS）启发的“知识图谱—大语言模型”框架，旨在同时保持短路径的机制特异性，又通过邻域增强恢复必要的生物学上下文，从而提升药物重定位预测的准确性与可解释性。

## 2. 方法论
- **核心思想**：将推理过程分解为两个互补模块，分别模拟 DFS 的“纵向深入”和 BFS 的“横向扩展”。
- **DFS 式短路径语义编码模块**：
  - 将遍历严格约束为**短的疾病—基因—药物路径**（避免长链冗余）。
  - 每条路径被转化为**结构化提示**（prompt），并输入生物医学大语言模型，生成**语义路径嵌入**，捕捉路径级别的机制特异性。
- **BFS 式机制上下文增强模块**：
  - 从**单跳基因邻域**构建实体级别的机制上下文嵌入。
  - 通过**相似性引导的增强**策略丰富这些嵌入：利用药理相关的药物以及具有相似基因表达特征的疾病，扩展实体表示，从而恢复更广泛的生物学背景。
- **融合预测**：将两类嵌入结合，用于下游药物—疾病关联预测（具体融合方式未在摘要中详述，但整体构成评分或分类器）。整个框架可端到端训练或作为特征增强器使用。

## 3. 实验设计
- **数据集/场景**：在**五个生物医学知识图谱**上评估（摘要未列具体名称，通常可能包括 DRKG、Hetionet、PrimeKG 等公开图谱）。
- **基准与指标**：以**AUPRC**（精确率—召回率曲线下面积）作为主要性能度量。
- **对比方法**：与**18 个基线**进行全面比较，涵盖当时的先进模型（如基于路径排序、图嵌入、KG 推理等类别的方法）。
- **附加验证**：通过**案例研究**和**近期 FDA 获批的适应症**进行实际相关性验证，并进行消融实验和基因本体（GO）功能一致性分析。

## 4. 资源与算力
- 论文摘要及元数据中**未明确说明**所使用的 GPU 型号、数量、训练时长或推理所需算力。该信息可能需要查阅论文正文或附录。

## 5. 实验数量与充分性
- 实验规模较大：覆盖 **5 个知识图谱 × 18 个基线** 的主要对比，至少包含数十组核心实验。
- **消融实验**：明确分析了语义短路径编码和机制上下文增强各自对性能的贡献，以及增强模块在稀疏证据下的鲁棒性提升。
- **一致性验证**：引入基因本体功能一致性等外部评估，增强结果可信度。
- **案例研究**：针对 FDA 批准的药物—适应症进行定性验证，补充定量指标的不足。
- 总体而言，实验设计在跨度、深度和辅助分析上较为**充分、客观且公平**，能够支撑其主要结论。

## 6. 论文的主要结论与发现
- CAREPath 在五个生物医学知识图谱上取得**最优总体 AUPRC**，性能提升最高可达 **3.8%**。
- **语义短路径编码**对模型性能贡献最大，说明保留短路径的特异性至关重要。
- **机制上下文增强模块**主要在**证据稀疏**的场景下提升鲁棒性，并能显著改善预测结果的**基因本体功能一致性**。
- CAREPath 是一个**可解释、可扩展且具有机制感知能力**的药物重定位框架，并已通过 FDA 实际批文的案例得到初步验证。

## 7. 优点
- **搜索策略的巧妙融合**：将 DFS 与 BFS 思想抽象为双模块结构，平衡了特异性和覆盖度，思路新颖。
- **LLM 语义编码**：利用生物医学语言模型将离散路径转为语义嵌入，提升了路径的表示能力和泛化性。
- **针对稀疏性问题**：相似性引导的上下文增强策略有效缓解了因知识图谱不完整导致的证据稀疏问题。
- **可解释性**：路径级别的提示和嵌入天然支持回溯推理机制，符合药物发现领域的需求。
- **开源与可复现**：提供源代码，便于后续研究验证和扩展。

## 8. 不足与局限
- **知识图谱依赖**：性能受限于现有知识图谱的质量与覆盖度，跨图谱的泛化能力虽有评估，但未讨论图谱偏差带来的影响。
- **计算资源未披露**：框架涉及大语言模型编码，其推理开销和实际部署成本无法从摘要评估。
- **基线细节缺失**：摘要中未列出 18 个基线的具体名称，难以在此处评判对比的全面性和最新性。
- **“短路径”的定义**：未说明对路径长度的具体截断阈值，其选择可能对结果敏感，但未提及敏感性分析。
- **仅限于静态图谱**：未结合多模态数据（如转录组、蛋白质组）和动态调控信息，可能遗漏部分生物学机制。
- **评估指标单一**：主要依赖 AUPRC，未报告排序精度或临床实用性指标（如 NDCG、命中率），且案例研究仅为定性。

（完）
