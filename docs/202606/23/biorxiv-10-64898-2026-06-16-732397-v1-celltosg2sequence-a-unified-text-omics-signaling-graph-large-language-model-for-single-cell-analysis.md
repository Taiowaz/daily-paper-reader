---
title: "CellTosg2Sequence: A Unified Text-Omics-Signaling-Graph Large Language Model for Single-Cell Analysis"
title_zh: CellTosg2Sequence：面向单细胞分析的统一文本-组学-信号-图大型语言模型
authors: "chen, w., Ye, M., Xu, T., Huang, D., Zhang, H., Li, H., Li, W., Chen, Y., Payne, P. R., Li, F."
date: 2026-06-22
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.16.732397v1.full.pdf"
tags: ["query:graph-llm"]
score: 9.0
evidence: 将文本先验知识和信号图谱与大型语言模型相结合，用于单细胞分析。
tldr: 现有单细胞大语言模型仅利用基因名文本，缺乏细胞定位、功能、疾病关联等生物医学先验知识，限制了解释能力。CellTosg2Sequence通过异构图编码器将大规模知识图谱注入细胞组学句子，并采用三阶段训练（KG锚定预训练、监督微调和本体层级奖励强化学习）实现文本-组学-信号图统一建模。该方法在多项基准测试中超越强基线，能以自由生成方式预测训练集外的细胞类型，且仅需轻量LoRA训练。该工作为单细胞分析提供了融合丰富先验与推理的统一框架，推动了模型可解释性和泛化性。
source: biorxiv
selection_source: fresh_fetch
motivation: 当前单细胞大语言模型仅依赖数值表达和基因名，缺少细胞定位、功能、疾病关联等生物医学先验知识。
method: 提出CellTosg2Sequence，通过异构图编码器将知识图谱化为虚拟tokens，结合三阶段训练（KG锚定预训练、监督微调、本体层级奖励的GRPO）增强推理。
result: 在多个基准和消融实验中显著超越主流基线，仅需轻量LoRA训练和统一检查点即可泛化到训练集外细胞类型。
conclusion: 首次将文本先验与信号图谱注入单细胞语言模型，提升了预测准确性与开放性，为整合生物知识的大规模模型提供新范式。
---

## 摘要
在基于单细胞（sc）的科学发现中，文本格式的生物医学先验知识和信号图对于注释和解读数值化单细胞组学数据以及生成可检验的新假设至关重要。现有单细胞大型语言模型（scLLM）的一个主要局限在于，它们依赖数值表达数据，仅以基因名称作为文本信号，而全面的生物医学先验——细胞定位、基因功能、疾病关联和信号交互模式——在模型输入中仍然缺失。我们提出了CellTosg2Sequence，一个文本先验和信号图增强的细胞-组学-句子语言模型。一个轻量级异构图编码器将精心构建的包含62,507个节点的生物医学知识图谱（KG）映射为紧凑的虚拟标记，并将这些标记前置到每个细胞句子中，使得语言模型能够以最小的序列长度开销依赖生物结构进行条件推理。我们采用三阶段目标训练CellTosg2Sequence：第一阶段在自回归语言模型预训练中锚定KG通道，利用Qwen2.5-32B自身的语言推理能力实现快速KG对齐；第二阶段通过带有KG锚定InfoNCE的监督微调对齐标签；第三阶段应用分组相对策略优化（GRPO），结合本体层次奖励，实现超越训练闭集词汇的自由生成式细胞类型预测。在多个基准测试和消融实验中，CellTosg2Sequence均优于强基线模型。所有结果均通过轻量级LoRA训练和单一统一检查点获得。

## Abstract
bioRxivLaTeXUnicodeabstract --- In single-cell (sc)-based scientific discovery, text-formatted biomedical prior knowledge and signaling graphs are essential for annotating and interpreting numeric sc-omics data and for generating novel testable hypotheses. A major limitation of existing single-cell large language models (scLLMs) is that they rely on numeric expression data with gene names as the only textual signal, while comprehensive biomedical priors -- cellular localization, gene function, disease associations, and signaling interaction patterns -- remain absent from the model input. We introduce CellTosg2Sequence, a textual-prior- and signaling-graph-augmented cell-omics-sentence language model. A lightweight heterogeneous graph encoder maps a curated 62,507-node biomedical knowledge graph (KG) into compact virtual tokens that are prepended to each cell sentence, allowing the language model to condition on biological structure with minimal sequence-length overhead. We train CellTosg2Sequence with a three-stage objective: Stage I anchors the KG channel under autoregressive language-model pretraining, leveraging Qwen2.5-32B's own language reasoning for rapid KG alignment; Stage II aligns labels via supervised fine-tuning with KG-anchored InfoNCE; Stage III applies Group Relative Policy Optimization (GRPO) with an ontology-hierarchy reward, enabling free-generation cell-type prediction that generalizes beyond the closed training vocabulary. Across multiple benchmarks and ablation experiments, CellTosg2Sequence outperforms strong baselines. All results are achieved with lightweight LoRA training and a single unified checkpoint.

---

## 论文详细总结（自动生成）

### 论文核心问题与整体含义

*   **研究背景**：单细胞组学数据分析依赖丰富的生物医学先验知识，如细胞定位、基因功能、疾病关联和信号通路交互信息。这些信息通常以文本或知识图谱形式存在。
*   **研究动机与核心问题**：现有的单细胞大型语言模型仅将数值化的基因表达与基因名称文本作为输入，完全忽略了上述关键的生物医学先验和信号图结构知识，导致模型解释力与知识推理能力受限。
*   **整体含义**：论文旨在将文本先验与信号图谱结构显式注入单细胞语言模型，构建一个能够感知和利用丰富生物结构的统一文本-组学-信号-图大型语言模型，从而增强单细胞分析的准确性与可解释性。

### 方法论

论文提出了 `CellTosg2Sequence`，核心思想是将大规模生物医学知识图谱映射为紧凑的虚拟标记，并前置到细胞组学句子上，使语言模型能够以结构化的生物背景信息进行条件推理。方法论包含以下关键技术细节和流程：

*   **异构图编码器与知识图谱映射**：
    *   构建了一个包含 62，507 个节点的大规模生物医学知识图谱。
    *   设计了一个轻量级异构图编码器，将该图谱压缩映射为一组紧凑的虚拟标记。
    *   这些虚拟标记被前置到每一个单细胞表达数据构成的“句子”前，使得模型能以极小的序列长度开销引入全面的图结构知识。

*   **三阶段训练策略**：
    *   **第一阶段：KG锚定预训练**。在自回归语言模型预训练目标下，固定基座模型如 `Qwen2.5-32B` 并训练图编码器，利用大模型自身的语言推理能力实现快速知识图谱对齐。
    *   **第二阶段：监督微调与KG锚定InfoNCE**。在标准的监督微调任务中，引入了一个基于知识图谱锚定的 `InfoNCE` 对比学习损失函数，以更好地对齐细胞表征与正确标签。
    *   **第三阶段：分组相对策略优化与本体层级奖励**。采用强化学习技术，设计基于本体层级结构的奖励函数，使模型能够以自由生成的方式预测细胞类型，泛化到训练集封闭词汇之外的类别。

### 实验设计

*   **场景与基准测试**：论文在多个未具名的单细胞分析基准测试上进行了评估，核心任务是细胞类型预测。
*   **对比方法**：论文将 `CellTosg2Sequence` 与多个强基线模型进行了比较，实验证明其性能显著超越这些基线。
*   **实验变体**：设计了消融实验，用于验证模型各组件如知识图谱通道、训练阶段的贡献。

### 资源与算力

论文明确指出，所有结果均基于基座模型 `Qwen2.5-32B`，并使用轻量级的 `LoRA` 训练技术，仅需一个统一的检查点即可完成。然而，文中未提供实现这些结果所使用硬件的具体型号与数量，也未给出详细的训练总时长。

### 实验充分性与客观性评估

*   **实验数量**：论文覆盖了多个基准测试、与强基线的对比以及消融实验，从多角度验证方法的有效性。
*   **充分性**：实验设计较为完整，不仅展示了最终性能，还通过三阶段训练和消融研究分析了方法各组成部分的贡献，较为充分。
*   **客观性与公平性**：文中提到与多个强基线进行对比并在多个基准上表现一致领先，且所有结果均来自统一检查点，这在一定程度上保证了比较的公平性。但由于未完全公开具体的实验配置与资源细节，无法进行更深入的公平性评估。

### 主要结论与发现

*   `CellTosg2Sequence` 首次成功地将大规模的文本先验知识与信号图谱结构注入到单细胞语言模型中。
*   该方法在多项基准测试上取得了超越现有强基线的优异性能。
*   通过轻量级`LoRA`训练与统一检查点，模型实现了高效、稳定的知识增强。
*   模型获得了开放式的细胞类型生成能力，能够泛化出训练集未见的细胞类型，实用性更强。

### 优点与亮点

*   **创新的输入模态融合**：巧妙地将知识图谱转化为虚拟标记，解决了异构多模态数据如文本、数值、图的统一建模问题，是方法论上的一大亮点。
*   **高效的训练范式**：采用“大模型加轻量级适配器”的`LoRA`训练范式，大幅降低了训练成本，同时保持了模型性能，具有较高的工程实用性。
*   **开放集生成能力**：通过本体层级奖励的强化学习，使模型突破分类头限制，实现自由生成式预测，是领先于许多前序工作的关键能力。
*   **全面的知识增强**：不再是简单的基因名匹配，而是引入了定位、功能、通路等多维度、结构化的生物医学先验，显著提升了模型的可解释性潜力。

### 不足与局限

*   **算力透明性缺失**：论文未报告关键的计算资源消耗，如GPU型号与数量、训练总时长，这使得其他研究者难以精确评估其训练成本与可复现性。
*   **知识图谱的覆盖度与偏差风险**：构建的知识图谱虽大，但其覆盖度和潜在的生物学偏见可能会影响模型在特定领域或罕见知识上的表现。论文未对该图谱本身的质量和偏差进行详细分析。
*   **应用限制**：作为一个复杂的重型模型，其在实际应用中，尤其是资源受限环境下的部署和推理延迟将是潜在的挑战。
*   **评估维度局限**：目前的评估集中于预测准确性，对于模型在生成“可检验新假设”如推断因果、药物靶点发现上的能力，缺乏深入、定量的下游任务验证。

（完）
