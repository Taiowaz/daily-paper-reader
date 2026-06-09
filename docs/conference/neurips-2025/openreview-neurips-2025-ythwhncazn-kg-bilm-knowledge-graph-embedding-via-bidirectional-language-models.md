---
title: "KG-BiLM: Knowledge Graph Embedding via Bidirectional Language Models"
title_zh: KG-BiLM：通过双向语言模型实现知识图谱嵌入
authors: "Zirui Chen, Xin Wang, Zhao Li, Wenbin Guo, Dongxiao He"
date: 2025-05-11
pdf: "https://openreview.net/pdf?id=yThwhNCaZN"
tags: ["query:graph-llm"]
score: 9.0
evidence: 融合知识图谱结构与双向语言模型以获取丰富语义
tldr: 现有方法或偏重结构或偏重语义，导致表示不完整。KG-BiLM设计双向知识注意力模块，消除因果掩码以允许token之间充分交互，并引入结构感知编码，使语言模型同时捕捉知识图谱的连通模式与文本语义。在多个标准知识图谱基准上，KG-BiLM的链接预测和实体分类性能显著超过仅结构或仅语义的方法，为知识增强语言模型提供了新思路。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ythwhncazn/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1361, \"height\": 533, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ythwhncazn/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1438, \"height\": 636, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ythwhncazn/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1189, \"height\": 450, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ythwhncazn/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 778, \"height\": 219, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ythwhncazn/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1452, \"height\": 762, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ythwhncazn/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1278, \"height\": 634, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ythwhncazn/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 526, \"height\": 261, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ythwhncazn/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 581, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ythwhncazn/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1476, \"height\": 1809, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ythwhncazn/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1493, \"height\": 1366, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ythwhncazn/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1439, \"height\": 902, \"label\": \"Table\"}]"
motivation: 现有知识表示方法未能同时充分捕获图谱结构与文本语义。
method: 提出双向语言模型框架，通过双向知识注意力融合图谱结构和语义信息。
result: 在知识图谱补全与推理任务上性能领先，消融实验验证各组件有效性。
conclusion: 结构信息与语言模型语义的深度融合是提升知识表示的关键。
---

## Abstract
Recent advances in knowledge representation learning (KRL) highlight the urgent necessity to unify symbolic knowledge graphs (KGs) with language models (LMs) for richer semantic understanding. However, existing approaches typically prioritize either graph structure or textual semantics, leaving a gap: a unified framework that simultaneously captures global KG connectivity, nuanced linguistic context, and discriminative reasoning semantics. To bridge this gap, we introduce KG-BiLM, a bidirectional LM framework that fuses structural cues from KGs with the semantic expressiveness of generative transformers. KG-BiLM incorporates three key components: (i) Bidirectional Knowledge Attention, which removes the causal mask to enable full interaction among all tokens and entities; (ii) Knowledge-Masked Prediction, which encourages the model to leverage both local semantic contexts and global graph connectivity; and (iii) Contrastive Graph Semantic Aggregation, which preserves KG structure via contrastive alignment of sampled sub-graph representations. Extensive experiments on standard benchmarks demonstrate that KG-BiLM outperforms strong baselines in link prediction, especially on large-scale graphs with complex multi-hop relations—validating its effectiveness in unifying structural information and textual semantics.

---

## 论文详细总结（自动生成）

好的，基于提供的论文内容，以下是对《KG-BiLM: Knowledge Graph Embedding via Bidirectional Language Models》的结构化深度总结。

### 1. 论文的核心问题与研究动机

论文针对当前**知识表示学习（KRL）** 领域的一个核心瓶颈：**如何在一个统一框架内，同时有效捕获知识图谱（KG）的全局结构性连接和语言模型（LM）的丰富语义理解**。

*   **现有方法局限**：
    *   **传统KGE方法**（如TransE、DistMult）仅基于结构化三元组，完全忽略词汇语义，难以处理长尾实体和适应异构下游任务。
    *   **基于编码器的LM**（如BERT）能注入上下文语义，但缺乏对图谱特定领域文本的预训练，且受限于局部上下文窗口，难以捕捉全局多跳关系。
    *   **基于解码器的LLM**（如LLaMA）可生成文本，但其单向生成范式阻碍了双向依赖关系的建模，且输出缺乏对图谱结构的显式约束，容易产生事实性错误。
*   **论文目标**：提出一个**混合架构 KG-BiLM**，旨在构建信息密度更高的嵌入，融合双向结构推理、局部语义保真度和全局拓扑一致性，并支持零样本编码能力。

### 2. 方法论：KG-BiLM 模型

KG-BiLM 核心思想是改造一个解码器式 Transformer，通过三个关键技术创新，将其从单向文本生成器转变为能同时对图谱结构和文本语义进行双向建模的统一框架。

*   **（i）双向知识注意力（Bidirectional Knowledge Attention, BKA）**
    *   **核心思想**：移除标准解码器中的因果掩码（causal mask），设计一种图谱感知的注意力掩码 `M_BKA`。
    *   **技术细节**：对于输入序列中的任意一对 token `(xi, xj)`，如果它们属于同一子图或在一定跳数阈值内存在关系路径，则 `M_BKA[i,j] = 0`（允许交互），否则为 `-∞`（禁止交互）。这使得模型能够在全序列和前/后文以及相连的图谱实体间进行双向注意力计算。
    *   **效果**：有效捕获了长距离、多跳的关系模式，增强了信息传播和嵌入的表达能力。

*   **（ii）知识掩码预测（Knowledge-Masked Prediction, KMP）**
    *   **核心思想**：在输入序列中策略性地掩码实体和文本 token，强制模型同时利用全局图谱拓扑和局部语言上下文来重建被掩码的部分。
    *   **关键技术 - 位置偏移损失（Position-Shifted Loss）**：模型不是基于当前位置 `hi` 来预测掩码 token `xi`，而是基于前一个位置的隐藏状态 `hi-1` 进行预测。损失函数定义为：`L_KMP = -Σ log pΘ(xi | hi-1)`。
    *   **效果**：这种偏移机制迫使模型必须从前后文和关联实体中聚合信息，模拟了生成时的因果条件，有效增强了跨模态推理和零样本泛化能力。

*   **（iii）对比图谱语义聚合（Contrastive Graph Semantic Aggregation, CGSA）**
    *   **核心思想**：通过对比学习，在嵌入空间中拉近语义/结构上相似的子图谱对，推远不相似的对，从而保持嵌入的判别力和全局语义边界。
    *   **技术细节**：对同一原始样本（子图谱或文本片段）应用随机的 Dropout 掩码，生成两个不同的视图 `z(1)` 和 `z(2)`。基于 InfoNCE 损失函数进行训练：`L_CGSA = -log[ exp(sim(z_k1, z_k2)/τ) / Σ exp(sim(z_k1, z_l2)/τ) ]`。
    *   **效果**：确保了实体嵌入在复杂关系和文本扰动下的稳定性与内聚性，提升了全局语义的表征能力。

### 3. 实验设计

论文在多个基准数据集上进行了全面的实验，以验证模型在纯结构推理和结构-语义融合推理上的能力。

*   **数据集**：
    *   **纯结构数据集**：**WN18RR** 和 **FB15k-237**，不含任何文本描述，用于测试模型的纯图结构学习能力。
    *   **语义增强数据集**：**FB15K-237N** 和 **Wikidata5M**，为每个实体提供了丰富的文本描述。其中 Wikidata5M 是大规模数据集，FB15k-237N 具有显著的长尾分布。
*   **评估任务与指标**：核心任务是**链接预测**。评估指标包括平均倒数排名（MRR）、平均排名（MR）和 Hits@k (k=1,3,10)。
*   **对比方法**：对比了三大类共18个以上的基线模型，覆盖面广，对比公平。
    *   **传统KGE方法**：TransE, DistMult, ComplEx, ConvE, TuckER, CompGCN, NBFNet等。
    *   **编码器基KRL方法**：KG-BERT, Pretrain-KGE, SimKGC, CSPromp-KG, KEPLER等。
    *   **解码器基KRL方法**：KG-S2S, CD (Contextualization Distillation), GPT-3.5, CP-KGC等。

### 4. 资源与算力

论文在附录E中明确给出了详细的硬件和软件环境。

*   **硬件配置**：使用了两块 NVIDIA H100 GPU (80 GB HBM3)，通过 NVLink 互联。主机配置为双路 Intel Xeon Silver 4416 CPU 和 512 GB RAM。
*   **软件环境**：PyTorch 2.0, CUDA 12.8, NCCL 2.16 等。

### 5. 实验数量与充分性

论文的实验设计**非常充分且系统**，从多个维度验证了模型的有效性。

*   **主要实验**：在**4个**不同规模和特性的数据集上进行了全面的性能对比，涉及超过18种基线模型，覆盖了纯图结构、语义增强和零样本三种核心场景。
*   **消融实验**：系统移除了三个核心组件（BKA, KMP, CGSA）中的一个，以精确量化每个模块的贡献，验证了架构创新的有效性。
*   **零样本实验**：在 Wikidata5M 的零样本设定下进行测试，这是对泛化能力最严格的检验。
*   **定性分析**：通过 t-SNE 可视化和注意力热力图，直观地展示了嵌入空间质量和双向注意力的工作模式。
*   **公平性**：对比对象涵盖了从经典KGE到最新LLM-KG融合方法的各流派SOTA模型，实验对比客观且具有代表性。

### 6. 主要结论与发现

*   **统一框架优势显著**：KG-BiLM 成功融合了图谱结构与文本语义，在多个基准测试中取得了最优性能。
*   **纯结构推理竞争力强**：在无文本的 WN18RR 数据集上，MRR 达到 68.2，超越所有基线。在 FB15k-237 上保持竞争力，但与专门的图模型 NBFNet 尚有差距。
*   **语义增强设定下性能领先**：在 FB15k-237N 和 Wikidata5M 上均取得 SOTA 结果，特别是在长尾实体和 Hits@1 指标上提升显著，证明了 KMP 和 CGSA 模块处理文本和长尾问题的有效性。
*   **零样本泛化能力突出**：在 Wikidata5M 零样本设定下，MRR 达到 0.748，远超 SimKGC 和 KEPLER，验证了 BKA 和 KMP 赋予的强泛化能力。
*   **模块贡献明确**：消融实验证实 BKA 模块贡献最大（尤其是多跳推理），其次是 KMP，CGSA 主要在提升高精度排序（Hits@10）上作用显著。

### 7. 优点

*   **创新性强**：将解码器Transformer改造为双向图-文联合建模框架，BKA、位置偏移的KMP等设计颇具巧思。
*   **动机清晰，论证有力**：从论文开篇的图1到各部分设计，清晰地指出现有方法缺陷并提出针对性解决方案。
*   **实验全面扎实**：覆盖四种数据集、三个任务场景、数十种基线模型和详尽的消融/可视化分析，结论极具说服力。
*   **性能领先**：在绝大多数实验设置下达到了SOTA性能，尤其是在更具挑战性的语义增强和零样本场景。

### 8. 不足与局限

*   **纯结构场景性能瓶颈**：在关系种类繁多（FB15k-237）且无文本信息的纯结构场景下，模型性能相较于顶尖的路径基模型（如NBFNet）仍有差距。作者指出可能是Attention机制在无语言线索时对关系语义的区分能力受限。
*   **对文本信息有依赖性**：模型的掩码重建和对比学习机制在设计时假设了弱文本上下文的存在，当完全缺乏文本时，无法完全发挥其潜力。
*   **实验统计信息缺失**：论文在检查列表中提到，由于未报告误差棒等统计显著性指标，这可能影响对结果稳定性的严谨判断。
*   **方法复杂性**：组合了 BKA、KMP 和 CGSA 三个模块，相对复杂，可能对训练调优和计算资源有更高要求。

（完）
