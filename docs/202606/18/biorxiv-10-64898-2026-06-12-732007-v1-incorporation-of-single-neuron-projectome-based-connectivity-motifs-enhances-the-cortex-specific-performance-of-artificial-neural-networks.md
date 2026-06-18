---
title: Incorporation of single-neuron projectome-based connectivity motifs enhances the cortex-specific performance of artificial neural networks
title_zh: 整合基于单神经元投射组的连接基序提升人工神经网络在皮层特异性任务中的表现
authors: "Sun, Y., Yao, W., Zhang, J., Song, W., Zhao, X., Hao, C., Chen, X., Zeng, S., Jia, S., Yang, Y., Xiao, X., Poo, M.-m., Xu, B., Zhang, T."
date: 2026-06-17
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.12.732007v1.full.pdf"
tags: ["query:graph-llm"]
score: 7.0
evidence: 使用脑连接模体（图模式）增强基于Transformer的大语言模型训练
tldr: 小鼠大脑单神经元连接组分析揭示了不同皮层区的三节点连接模体特异轮廓。提出CINA算法将自然模体融入RNN和Transformer，发现皮层模体显著提升抗噪分类和运动学习任务表现，且皮层特异模体进一步增强相关功能任务，通过人工增大模体偏差可强化效果，在LLM的语言问答和脑信号解码中验证。图论分析揭示了模块化和小世界特性涌现。该研究不仅提供了连接组启发的ANN架构优化方法，还揭示了特定皮层模体轮廓的功能重要性。
source: biorxiv
selection_source: fresh_fetch
motivation: 探索小鼠皮层单神经元连接组的三节点模体特异性是否能优化人工神经网络架构与功能对应。
method: 开发CINA算法将单神经元连接组的皮层特异三节点模体融入RNN和Transformer，并在多个任务上与随机连接网络对比。
result: 皮层模体提升RNN抗噪分类与运动学习性能，皮层特异模体进一步增强相关功能，增大偏差强化效果，在LLM问答和脑信号解码中验证，并驱动网络出现模块化和小世界特性。
conclusion: 本研究证实连接组启发的ANN架构优化有效，并揭示特定皮层模体轮廓的功能重要性，为类脑计算提供参考。
---

## 摘要
自然神经网络的构建原理可为人工神经网络的新架构设计提供启发。对小鼠大脑单神经元连接组的分析揭示了不同皮层区域和海马结构中三节点连接基序的独特分布。我们开发了一种连接组启发的神经网络算法（"CINA"），将自然连接基序整合到以循环神经网络和基于Transformer的大语言模型为代表的人工神经网络算法中。研究发现，与随机连接的循环神经网络相比，整合皮层基序的平均分布可提升网络在抗噪分类和运动学习基准任务中的表现。值得注意的是，整合皮层特异性基序可进一步提升循环神经网络在与该皮层功能相关任务上的表现，且这一效应可通过人为增大基序分布的偏差而增强。在使用Motif-Transformer的大语言模型上进行自然语言问答和脑信号解码任务时，也验证了类似的实验结果。图论分析表明，整合自然基序促进了人工神经网络中模块化与小世界特性的涌现。综上，我们不仅展示了连接组启发的神经网络架构优化，还揭示了不同皮层中特定基序分布的功能意义。

## Abstract
The organizational principles of natural neural networks could inspire the new architecture design of artificial neural networks (ANNs). Analysis of single-neuron connectomes of mouse brains revealed distinct profiles of three-node connectivity motifs in various cortical areas and hippocampal formation. A connectome-informed neural network algorithm ("CINA") was developed to incorporate natural connectivity motifs into ANN algorithms represented by recurrent neural network (RNN) and transformer-based large language model (LLM). We found that incorporation of the average profile of cortical motifs improved the RNN's performance in noise-resistant categorization and motor learning benchmark tasks, as compared with RNNs with random connectivity. Notably, incorporating cortex-specific motifs further elevated the RNN's performance in tasks related to the cortical function, and this effect was enhanced by artificially increasing the bias in the motif profile. Similar experimental results were verified on an LLM using Motif-Transformer for natural language question answering and brain-signal decoding tasks. Graph-theoretic analyses showed that incorporating natural motifs drove the emergence of modular and small-world properties in ANNs. Together, we demonstrated not only connectome-inspired optimization of ANN architecture but also functional significance of specific motif profiles in various cortices.