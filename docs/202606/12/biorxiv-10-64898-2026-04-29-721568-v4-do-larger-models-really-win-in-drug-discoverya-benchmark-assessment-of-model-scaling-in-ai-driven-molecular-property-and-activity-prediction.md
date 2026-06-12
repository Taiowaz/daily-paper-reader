---
title: Do Larger Models Really Win in Drug Discovery?A Benchmark Assessment of Model Scaling in AI-Driven Molecular Property and Activity Prediction
title_zh: 大模型真的在药物发现中胜出吗？AI驱动的分子性质与活性预测中模型规模的基准评估
authors: "Guo, J., Ding, S."
date: 2026-06-08
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.29.721568v4.full.pdf"
tags: ["query:graph-llm"]
score: 7.0
evidence: 在分子图结构数据上评估大型语言模型进行分子性质预测，并与图神经网络比较
tldr: "随着药物发现中大规模分子基础模型兴起，是否模型越大预测越好？本研究构建涵盖26个ADME/毒性/活性端点、三种分割协议的基准，系统对比经典ML、GNN、预训练序列模型与LLM-SAR方法。结果显示经典ML在47.4%的比较中获胜，大模型仅在困难分割与低数据场景展现推理价值，且优势依赖训练配置。表明预测性能取决于模型-任务-验证场景的匹配，而非单纯规模扩展。"
source: biorxiv
selection_source: fresh_fetch
motivation: 验证“更大预训练模型优于紧凑模型”的假设，评估不同规模模型在分子性质预测中的真实表现。
method: 在26个端点、3种分割协议（随机/骨架/结构分离）下，对比经典ML、GNN、预训练序列模型与LLM-SAR的预测性能。
result: "经典ML获胜最多（47.4%），大模型仅在困难分割及低数据SAR推理中占优，且小差异不具决定性。"
conclusion: 紧凑专用模型仍具竞争力，大模型价值在于推理而非通用预测，效果取决于模型与任务和验证场景的适配。
---

## 摘要
分子基础模型和大语言模型（LLM）的快速增长鼓励了一种以规模为中心的AI药物发现观，即预期更大的预训练模型将取代针对单个任务训练的基于经典机器学习（经典ML）和图神经网络（GNN）的紧凑化学信息学模型。我们在26个端点（分组为ADME、毒性和生物活性类别）上检验这一假设，覆盖165541条端点级化合物标签记录。基准包含78个端点和划分条目，对应26个端点在三种划分协议下的评估：随机、Murcko骨架和结构分离的五折交叉验证（CV）。按从易到难的顺序，这些划分分别近似于在封闭库上的回顾性评估、从苗头化合物到先导化合物的骨架扩展，以及在新化学型上的库扩展。每个条目提供任务和指标两项比较，总计156项比较。在这些比较中，经典ML提供了最佳表现条目的最大份额（47.4%），其次是预训练分子序列模型（28.8%）、GNN（21.8%）和基于LLM的SAR基线（1.9%）。经典ML在随机划分插值中占主导地位，并保持整体上最大的赢家家族。在主要最优保留读出下，GNN和序列模型在选定的较难划分协议中具有竞争力，但在固定最终窗口读出下，它们的严格赢家份额下降，表明部分收益取决于训练设置和模型选择。配对自助法分析表明，不应将单个模型间的微小数值差异解读为决定性胜利。训练折叠中的SAR知识改善了许多GPT5.5-SAR和Opus4.7-SAR指标，但并未使基于规则的推理成为监督预测器的通用替代品。紧凑的专业化模型在分子性质和活性预测中仍然非常有效。较大的模型在低数据场景下的SAR解释和推理中增加价值，但预测性能取决于模型、任务和验证场景之间的匹配，而不仅仅取决于规模。

## Abstract
The rapid growth of molecular foundation models and large language models (LLMs) has encouraged a scale centred view of AI in drug discovery, in which larger pretrained models are expected to supersede compact cheminformatics models based on classical machine learning (classical ML) and graph neural networks (GNNs) trained for individual tasks. We test this assumption across 26 endpoints grouped into ADME, toxicity and bioactivity classes, covering 165,541 endpoint level compound label records. The benchmark contains 78 endpoint and split entries, corresponding to 26 endpoints evaluated under three split protocols: random, Murcko scaffold and structure separated 5-fold cross validation (CV). Ordered from easiest to hardest, these splits approximate retrospective evaluation on a closed library, scaffold expansion in hit to lead, and library expansion on novel chemotypes. Each entry contributes two task and metric comparisons, giving 156 comparisons in total. Across these comparisons, classical ML provides the largest share of best performing entries (47.4%), followed by pretrained molecular sequence models (28.8%), GNNs (21.8%) and LLM based SAR baselines (1.9%). Classical ML dominates random split interpolation and remains the largest winner family overall. GNN and sequence models are competitive in selected harder split protocols under the primary optimal held-out readout, but their strict winner shares decrease under a fixed final-window readout, indicating that some of these gains depend on training settings and model selection. Paired bootstrap analyses indicate that small numerical differences between individual models should not be read as decisive victories. SAR knowledge from training folds improves many GPT5.5-SAR and Opus4.7-SAR metrics but does not make rule based reasoning a universal substitute for supervised predictors. Compact specialized models remain highly effective for molecular property and activity prediction. Larger models add value for SAR interpretation and reasoning in low data settings, but predictive performance depends on the fit among model, task and validation scenario, not on scale alone.