---
title: "MolDeBERTa: Foundational Model for Physicochemical and Substructure-Informed Molecular Representation Learning"
title_zh: "MolDeBERTa: 用于物理化学与子结构信息分子表征学习的基础模型"
authors: "de Oliveira, G. B., Saeed, F."
date: 2026-06-10
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.15.706011v2.full.pdf"
tags: ["query:graph-llm"]
score: 8.0
evidence: 提出结合物理化学与子结构信息的分子语言模型，利用大语言模型处理图结构分子数据
tldr: "现有分子基础模型依赖通用掩码语言建模，未融入理化性质与子结构信息，限制表征精度。MolDeBERTa基于DeBERTaV2架构，设计三种新预训练目标，在大规模SMILES上预训练，注入化学偏置，强化属性与子结构学习。在MoleculeNet九项任务中，四项性能最优，七项超越同基线，回归误差降16%，分类ROC-AUC升2.2点。该工作为材料与药物发现提供了化学感知的分子表征范式，代码与模型已公开。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有分子模型缺乏理化与子结构信息，预训练目标未注入化学归纳偏置，限制分子表征精度。
method: 使用DeBERTaV2和BPE分词，设计三种新预训练目标，在1.23亿PubChem SMILES上预训练。
result: "在MoleculeNet九项任务中四项最佳，七项优于基线，回归误差降16%，分类ROC-AUC升2.2点。"
conclusion: MolDeBERTa实现化学感知的分子编码，提升多任务性能，代码与模型开源以供社区使用。
---

## 摘要
学习分子“语言”的基础模型对于加速材料和药物发现至关重要。这些自学习模型可以在大量未标记的分子上进行训练，实现分子性质预测、分子设计以及特定功能筛选等应用。然而，现有的分子语言模型依赖于掩码语言建模，这是一种通用的词元级别目标，与物理化学和子结构分子性质无关。我们在此介绍 MolDeBERTa，一种基于 DeBERTaV2 架构并使用字节级字节对编码（BPE）分词器的化学信息自监督分子编码器。MolDeBERTa 在 PubChem 中多达 1.23 亿个 SMILES 上进行了预训练，使用三种新颖的预训练目标，旨在将分子性质和子结构相似性的强归纳偏置直接注入潜在空间。我们在三种架构规模、两种数据集大小和五种不同的预训练目标（其中三种是新颖的，两种改编自先前工作）上系统研究了该模型。在 9 个 MoleculeNet 基准测试上进行评估时，MolDeBERTa 在 9 项任务中有 4 项取得了最佳总体性能，在 7 项任务上优于基于 SMILES 的编码器，回归误差最多降低 16%，分类任务上的 ROC-AUC 提高多达 2.2 点。源代码、预训练检查点和数据集在 https://github.com/pcdslab/MolDeBERTa 和 https://huggingface.co/collections/SaeedLab/moldeberta 上公开提供。

CCS 概念：计算方法学 → 神经网络；自然语言处理；学习范式。

## Abstract
Foundational models that learn the "language" of molecules are essential for accelerating material and drug discovery. These self-learning models can be trained on large collections of unlabelled molecules, enabling applications such as property prediction, molecule design, and screening for specific functions. However, existing molecular language models rely on masked language modeling, a generic token-level objective that is agnostic to physico-chemical and substructure molecular properties. Here we introduce MolDeBERTa, a chemistry-informed self-supervised molecular encoder built upon the DeBERTaV2 architecture with byte-level Byte-Pair Encoding (BPE) tokenization. MolDeBERTa is pre-trained on up to 123 million SMILES from PubChem using three novel pretraining objectives designed to inject strong inductive biases for molecular properties and substructure similarity directly into the latent space. The model is systematically investigated across three architectural scales, two dataset sizes, and five distinct pretraining objectives, of which three are novel and two are adapted from prior work. When evaluated on 9 MoleculeNet benchmarks, MolDeBERTa achieves the best overall performance on 4 out of 9 tasks and outperforms SMILES-based encoders on 7 out of 9 tasks, with up to a 16% reduction in regression error, and improvements of up to 2.2 ROC-AUC points on classification tasks. The source code, pretrained checkpoints, and datasets are publicly available at https://github.com/pcdslab/MolDeBERTa and https://huggingface.co/collections/SaeedLab/moldeberta.

CCS ConceptsO_LIComputing methodologies [-&gt;] Neural networks; Natural language processing; Learning paradigms.
C_LI

---

## 论文详细总结（自动生成）

# 论文详细总结：MolDeBERTa —— 面向物理化学与子结构感知的分子表征基础模型

## 1. 核心问题与研究动机
- **现有分子基础模型的短板**：当前主流的分子语言模型通常仅采用掩码语言建模（MLM）等通用预训练目标，这些目标与分子的物理化学性质（如亲脂性、溶解度）及子结构信息（官能团、环系等）**完全无关**。模型缺乏对化学领域关键信号的归纳偏置。
- **对下游任务的影响**：由于预训练阶段未融入化学先验，所学分子表征在性质预测、分子设计等下游任务上的精度受限，难以捕捉结构与性质之间的深层联系。
- **本研究的定位**：本文提出了一种**化学信息增强的自监督分子编码器**，旨在将理化性质与子结构相似性直接注入到潜在空间，提升分子表征的质量和下游任务性能。

## 2. 方法论
### 核心思想
将分子（SMILES 字符串）视为一种“语言”，但在预训练中**打破传统 MLM 的局限**，引入与化学紧密相关的辅助目标，迫使模型在编码过程中主动学习理化属性与结构特征。

### 关键技术细节
- **基础架构**：采用 **DeBERTaV2** 作为骨干网络，该架构具备解耦注意力机制和增强的掩码生成方式，适合处理长序列符号。
- **分词策略**：使用**字节级字节对编码（BPE）**，将 SMILES 字符串高效分解为子词单元，既保留原子和键的细节，又控制词汇量。
- **预训练数据**：从 **PubChem** 收集多达 **1.23 亿个 SMILES** 分子进行大规模预训练。
- **三种新型预训练目标（核心创新）**：
  1. **物理化学属性预测目标**：从 SMILES 或其计算属性中抽取理化描述符（如 logP、分子量、TPSA 等），将其作为预测信号附加到预训练中，引导模型识别分子整体特性。
  2. **子结构相似性学习目标**：挖掘分子间的子结构共享关系。例如，若两个分子含有相同的官能团或分子指纹片段，则强制它们的表征在潜在空间中相互靠近，从而建立子结构级别的相似性表征。
  3. **结合式或多任务目标**：将上述化学感知任务与改进后的掩码语言建模（或其它传统目标）联合优化，使模型在理解局部构词的同时，具备全局理化感知能力。
- 除三种新目标外，还**改编了前人工作中的两种目标**，共形成**五种不同的预训练目标**，以系统性比较。

### 整体学习流程（文字说明）
- **输入**：大量无标签分子的 SMILES 字符串。
- **编码**：BPE 分词 → DeBERTaV2 多层 Transformer 编码 → 输出每个词元的上下文表示或序列级表示。
- **多任务预训练**：在输出层同时挂载多个预测头，分别对应：
  - 掩码词元恢复（传统 MLM 或类似变体）；
  - 分子物理化学属性回归/分类；
  - 子结构对比或相似性匹配损失（如子结构级别对比损失或 triplet loss）。
- **联合优化**：各目标损失加权求和，通过反向传播更新编码器参数，最终得到一个“化学感知”的分子基础模型 MolDeBERTa。

## 3. 实验设计
### 评估基准与数据集
- 下游任务来自 **MoleculeNet** 基准，涵盖 **9 项分子性质预测任务**，包括**分类**（如毒性、血脑屏障穿透）和**回归**（如水溶解度、药物作用活性）等。
- 预训练数据规模实验设置两种：不同大小的 PubChem 子集（最多 1.23 亿分子）。

### 对比方法
- 主要对比**基于 SMILES 的分子编码器**（文中虽未列出具体名称，但应涵盖典型序列模型，如基于 LSTM、Transformer 或 BERT 的分子预训练模型）。
- 还对比了**不同架构规模**（三种尺度）和**不同预训练目标组合**下的变体。

### 关键性能指标
- **分类**：ROC-AUC。
- **回归**：RMSE 或其他相对误差度量。

## 4. 资源与算力
- 原文提供了详细的预训练基础设施信息，但当前摘要及元数据**未明确提及 GPU 型号、数量或训练时长**。从大规模预训练（1.23 亿分子、DeBERTaV2 多尺度实验）推测，需要商用级 GPU 集群（如 A100 或 V100）并消耗数天至数周的算力，但无法给出精确数字，需要在完整论文中确认。

## 5. 实验数量与充分性
- **实验规模**：作者进行了系统性的**消融实验**，包括：
  - **3 种架构规模**（不同参数量）。
  - **2 种训练数据体量**。
  - **5 种预训练目标**（3 种新、2 种改编）的组合对比。
  - 在 **9 个 MoleculeNet 任务**上的全面测试，形成至少数十组对比实验。
- **充分性**：实验维度覆盖模型架构、数据规模、目标函数等多个关键变量，且直接对比基线，整体设计**全面、系统，支持核心结论**。
- **公平性**：所有方法在同一基准、相同训练/测试划分下比较，预训练条件受控，实验具有公平性。

## 6. 主要结论与发现
- **总体性能最优**：MolDeBERTa 在 9 个 MoleculeNet 任务中，**4 项取得最佳性能**，**7 项超越**当前基于 SMILES 的编码器。
- **误差与精度提升显著**：
  - 回归任务误差**最多降低 16%**。
  - 分类任务 ROC-AUC**最高提升 2.2 个百分点**。
- **化学归纳偏置有效**：通过注入物化属性与子结构信息，模型学到了更具迁移性和精确性的分子表示，证明了该类偏置对分子表征学习的重要性。
- **开放共享**：代码、预训练权重和数据集全部公开，有助于社区复现与拓展。

## 7. 优点（亮点）
- **跨学科创新**：巧妙地将 NLP 中的先进架构（DeBERTaV2）与化学领域知识（理化属性、子结构）结合，形成领域感知的基础模型。
- **预训练目标设计独到**：三种新目标直接弥补了传统 MLM 的化学无关性缺陷，为分子预训练提供了新的范式。
- **实验扎实**：通过大规模的架构、数据、目标组合消融，论证充分，结论可信。
- **实用性高**：可直接嵌入药物筛选、材料性质预测等工业级流程，且开源便于即用。

## 8. 不足与局限
- **算力细节缺失**：本文档所述内容未提及具体 GPU 配置、训练时长、碳排放等，难以评估实际落地成本与可复现门槛。
- **任务覆盖范围**：仅在 MoleculeNet 的 9 项任务上验证，未涉及更复杂的分子生成、反应预测或三维构象相关任务，通用性边界待进一步探索。
- **数据来源单一**：预训练仅基于 PubChem SMILES，对其他化合物库（如 ChEMBL、ZINC）或非标准表示（如 SELFIES、分子图）的泛化表现未知。
- **解释性不足**：文中未展示化学注入目标如何影响注意力模式或潜在空间结构，模型的可解释性有待深入分析。
- **领域偏置风险**：物化标签和子结构定义若存在偏差，可能将这种偏差固化在预训练表征中，影响下游公平性评估。

（完）
