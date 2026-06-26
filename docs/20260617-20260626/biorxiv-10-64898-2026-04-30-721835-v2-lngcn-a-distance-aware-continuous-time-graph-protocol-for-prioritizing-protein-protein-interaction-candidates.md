---
title: "LNGCN: a distance-aware continuous-time graph protocol for prioritizing protein-protein interaction candidates"
title_zh: LNGCN：一种距离感知的连续时间图协议，用于对蛋白质-蛋白质相互作用候选进行优先级排序
authors: "Xiao, Y., Zheng, Y., Hua, Y., Peng, J., Liu, J., Qu, Y., Xu, J., Fu, R., Qian, Q., Zhao, M., Zhang, X., Zhao, J., Yao, Y., Kosar, M., Ke, Y., Chi, Y."
date: 2026-06-25
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.30.721835v2.full.pdf"
tags: ["query:dynamic-g"]
score: 7.0
evidence: 连续时间图协议与液体神经动力学建模图演化
tldr: 现有PPI预测方法依赖离散消息传递，存在过平滑和校准差的问题。LNGCN将残基级结构图与液体神经动力学结合，利用径向距离驱动连续图演化，并通过层次校准输出可解释概率。在多种基准上表现稳健，校准分数能对FGF23-FGFR1c-Klotho等复合物进行合理排序，并用实验证实了TPR相关互作。该协议为PPI候选提供了实用的优先排序工具。
source: biorxiv
selection_source: fresh_fetch
motivation: 传统图方法在PPI预测中常因离散传递和表示过平滑导致性能受限，且置信度校准不足，难以指导实验。
method: 提出LNGCN，集成残基结构图与液体神经网络，以径向距离为信号驱动连续时间图演化，后接层次校准模块。
result: 在平衡、极不平衡和跨物种数据上均取得稳健性能，校准分数在多个生物复合体排序合理，并实验验证了ELAVL1-TPR和RALY-TPR互作。
conclusion: LNGCN为PPI候选提供了一种有效且校准良好的优先排序方案，助力湿实验筛选。
---

## 摘要
蛋白质-蛋白质相互作用（PPI）的准确高通量预测对于阐明细胞机制和确定实验验证的优先次序至关重要。当前基于图的方法通常依赖于离散消息传递，面临表示过度平滑问题，并且提供的置信分数校准不佳。我们提出了LNGCN，一种距离感知的连续时间图协议，该协议将残基层次的结构图与液态神经动力学相结合，以模拟空间异质的相互作用模式。残基径向距离被用作连续图演化的显式驱动信号，而分层校准则将原始模型输出转换为可解释的相互作用概率。在平衡、高度不平衡和跨物种的基准测试中，LNGCN实现了稳健的预测性能。重要的是，校准后的分数在FGF23-FGFR1c–Klotho复合物、SHP2相关信号相互作用以及Tdk1寡聚态依赖性结合中支持了生物学上合理的优先排序。在以TPR为中心的实验案例研究中，LNGCN恢复了已知的TPR相关伙伴，并优先考虑了ELAVL1-TPR和RALY-TPR，它们的物理相互作用随后通过实验验证得到证实。这些结果表明，LNGCN可以作为对PPI候选进行优先排序的实用协议。

## Abstract
Accurate high-throughput prediction of protein-protein interactions (PPIs) is essential for mapping cellular mechanisms and prioritizing experimental validation. Current graph-based methods often rely on discrete message passing, suffer from representation over-smoothing, and provide poorly calibrated confidence scores. We present LNGCN, a distance-aware continuous-time graph protocol that integrates residue-level structural graphs with liquid neural dynamics to model spatially heterogeneous interaction patterns. Residue radial distance is used as an explicit driving signal for continuous graph evolution, while hierarchical calibration converts raw model outputs into interpretable interaction probabilities. Across balanced, highly imbalanced, and cross-species benchmarks, LNGCN achieved robust predictive performance. Importantly, the calibrated scores supported biologically coherent prioritization in the FGF23-FGFR1c--Klotho complex, SHP2-associated signaling interactions and Tdk1 oligomeric-state-dependent binding. In a TPR-centered experimental case study, LNGCN recovered known TPR-associated partners and prioritized ELAVL1-TPR and RALY-TPR, whose physical interactions were subsequently confirmed via experimental validation. These results indicate that LNGCN can serve as a practical prioritization protocol for PPI candidates.