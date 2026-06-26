---
title: "Drug-Prot: A query system for statistical inference of drug effects and interactions in dynamic proteomic networks"
title_zh: "Drug-Prot: 动态蛋白质组网络中药物效应与相互作用的统计推断查询系统"
authors: "Ulmer, M., Sun, R., Qian, L., Aebersold, R., Guo, T., Buehlmann, P."
date: 2026-06-22
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.17.732914v1.full.pdf"
tags: ["query:dynamic-g"]
score: 7.0
evidence: 从时间序列扰动蛋白质组学重建有向时序蛋白质依赖网络
tldr: 开发有效的联合疗法需要理解药物效应及药物间相互作用。Drug-Prot是一个计算框架，利用来自18种乳腺癌细胞系、63种单药和59种药物组合在6、24、48小时的大规模扰动蛋白质组学数据，量化因果药物效应，重建有向时间蛋白依赖网络。该框架通过交互式网络应用，允许用户针对自定义蛋白集查询，提供经校正的单药和组合效应p值及动态网络，显著降低多重检验负担，且无需访问原始数据。应用案例中，将不变性正则化随机森林用于三阴性乳腺癌识别药物响应蛋白，Drug-Prot查询揭示了药物特异性效应和蛋白网络层面的相互作用。Drug-Prot为连接候选因果蛋白与可操作药物组合提供了便捷工具。
source: biorxiv
selection_source: fresh_fetch
motivation: 联合疗法开发需解析药物效应与相互作用，但现有方法面临多重检验负担高且缺乏靶向蛋白动态网络分析工具。
method: Drug-Prot利用63种单药和59种组合在18种乳腺癌细胞系上的扰动蛋白质组数据，估计药物效应并重建有向时间依赖网络，通过交互式应用实现自定义蛋白集查询与多重检验校正。
result: 在三阴性乳腺癌中，应用不变性正则化随机森林识别与药物反应相关的蛋白，Drug-Prot查询揭示了这些蛋白的药物特异性和组合效应，并给出有向依赖关系。
conclusion: Drug-Prot以公开软件形式提供，无需原始数据，显著减轻多重测试负担，为研究者将候选蛋白与可操作药物组合联系起来提供高效工具。
---

## 摘要
理解药物效应和药物间相互作用对于开发联合疗法至关重要。我们提出了Drug-Prot，一个利用大规模扰动蛋白质组学量化因果药物效应、药物间相互作用及动态蛋白质关系的计算框架。通过使用63种单药和59种药物组合在6小时、24小时和48小时作用于18种乳腺癌细胞系的数据，Drug-Prot估计药物对蛋白质表达的影响，并重建有向的时间蛋白质依赖网络。

该公开软件支持对用户定义的蛋白质集进行靶向分析，显著降低了多重检验的负担。通过交互式网络应用，用户可获得单药和组合效应的校正p值、有向时间依赖网络以及可下载的结果，无需访问底层蛋白质组数据集。

作为一个用例，我们将不变性正则化随机森林应用于三阴性乳腺癌细胞系，以识别与药物反应相关的蛋白质。在Drug-Prot中查询这些蛋白质揭示了在蛋白质网络层面上的药物特异性效应和相互作用效应，展示了该框架如何将候选因果蛋白质特征与可操作的药物组合联系起来。

## Abstract
Understanding drug effects and drug-drug interactions is essential for developing combination therapies. We present Drug-Prot, a computational framework that leverages large-scale perturbation proteomics to quantify causal drug effects, drug-drug interactions, and dynamic protein relationships. Using data from 63 single drugs and 59 drug combinations applied to 18 breast cancer cell lines at 6, 24, and 48 hours, Drug-Prot estimates drug effects on protein expression and reconstructs directed temporal protein dependency networks.

The publicly available software enables targeted analyses of user-defined protein sets, substantially reducing the multiple-testing burden. Through an interactive web application, users obtain corrected p-values for single-drug and combination effects, directed temporal dependency networks, and downloadable results without requiring access to the underlying proteomic dataset.

As a use case, we apply invariance-regularized Random Forests to triple-negative breast cancer cell lines to identify proteins associated with drug response. Querying these proteins in Drug-Prot reveals drug-specific and interaction effects at the protein-network level, illustrating how the framework links candidate causal protein features to actionable drug combinations.