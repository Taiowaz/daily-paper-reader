---
title: "FSTLLM: Spatio-Temporal LLM for Few Shot Time Series Forecasting"
title_zh: FSTLLM：用于少样本时间序列预测的时空大型语言模型
authors: "YUE JIANG, Yile Chen, Xiucheng Li, Qin Chao, SHUAI LIU, Gao Cong"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=oyoiHf51es"
tags: ["query:graph-llm"]
score: 8.0
evidence: 结合时空图神经网络与大型语言模型进行少样本时间序列预测。
tldr: 针对时间序列预测在少样本场景下性能受限的问题，提出FSTLLM框架，将时空图神经网络与大型语言模型结合，利用语言模型的上下文知识增强少样本学习。在多个真实数据集上，FSTLLM显著优于现有模型，有效缓解数据不足问题，推动了LLM在图结构时空数据中的应用。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-oyoihf51es/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1709, \"height\": 660, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oyoihf51es/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1716, \"height\": 831, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oyoihf51es/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1713, \"height\": 1045, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oyoihf51es/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1711, \"height\": 1194, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-oyoihf51es/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1612, \"height\": 1109, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oyoihf51es/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1248, \"height\": 156, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oyoihf51es/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1597, \"height\": 1658, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oyoihf51es/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 709, \"height\": 172, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oyoihf51es/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 713, \"height\": 208, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oyoihf51es/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1621, \"height\": 230, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oyoihf51es/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 731, \"height\": 458, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oyoihf51es/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1587, \"height\": 1259, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oyoihf51es/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1540, \"height\": 1875, \"label\": \"Table\"}]"
motivation: 少样本时间序列预测需要同时捕捉时空依赖和利用外部知识。
method: FSTLLM结合时空图神经网络与LLM，利用上下文知识嵌入进行少样本学习。
result: 在多个真实数据集上，FSTLLM显著优于现有方法，预测误差更低。
conclusion: LLM与图神经网络的融合能有效赋能少样本时空预测任务。
---

## Abstract
Time series forecasting fundamentally relies on accurately modeling complex interdependencies and shared patterns within time series data. Recent advancements, such as Spatio-Temporal Graph Neural Networks (STGNNs) and Time Series Foundation Models (TSFMs), have demonstrated promising results by effectively capturing intricate spatial and temporal dependencies across diverse real-world datasets. However, these models typically require large volumes of training data and often struggle in data-scarce scenarios. To address this limitation, we propose a framework named Few-shot Spatio-Temporal Large Language Models (FSTLLM), aimed at enhancing model robustness and predictive performance in few-shot settings. FSTLLM leverages the contextual knowledge embedded in Large Language Models (LLMs) to provide reasonable and accurate predictions. In addition, it supports the seamless integration of existing  forecasting models to further boost their predicative capabilities. Experimental results on real-world datasets demonstrate the adaptability and consistently superior performance of FSTLLM over major baseline models by a significant margin. Our code is available at: https://github.com/JIANGYUE61610306/FSTLLM.

---

## 论文详细总结（自动生成）

好的，作为资深学术论文分析助手，我将对提供的论文《FSTLLM: Spatio-Temporal LLM for Few Shot Time Series Forecasting》进行结构化、深入和客观的总结。

---

### 1. 论文的核心问题与整体含义

*   **研究动机与背景**：当前先进的时间序列预测模型，如时空图神经网络（STGNNs）和时间序列基础模型（TSFMs），虽然在捕捉数据中的时空依赖性方面表现优异，但它们通常是**数据饥渴型**的，需要海量训练数据。
*   **核心问题**：在现实世界的许多场景中，收集大规模训练数据耗时且昂贵，导致这些模型在**数据稀缺的少样本（Few-Shot）场景下性能下降**。此外，现有模型大多仅依赖数值型输入，**未能有效整合诸如地理信息、城市上下文和人类行为模式等现实世界的外部知识**，限制了预测精度的进一步提升。
*   **整体含义**：论文提出了**FSTLLM（Few-shot Spatio-Temporal Large Language Models）**框架，旨在利用大型语言模型（LLMs）中蕴含的丰富上下文知识和推理能力，来增强少样本场景下多元时间序列预测的鲁棒性和准确性。这项工作为将LLM应用于图结构化的时空数据预测任务、并有效缓解数据不足问题，提供了一个新颖且灵活的解决方案。

### 2. 论文提出的方法论

FSTLLM的核心思想是**利用LLM来增强时空图神经网络（STGNN）的图结构学习，并校准其预测结果**，以此实现对时空依赖和外部知识的联合建模。该框架包含三个主要模块：

*   **LLM增强的图构建模块（LLM-Enhanced Graph Construction Module）**：
    *   **核心思想**：抛弃传统STGNNs仅依赖数值数据学习节点间关系的做法，转而利用LLM从节点相关的**文本描述**（如停车场费率、位置、用户评论）中提取语义丰富的上下文信息来构建图结构。
    *   **关键技术细节**：
        1.  使用预训练的LLM（LLaMA-2-7B）处理每个时间序列通道（节点）的文本文件，提取最终层的隐状态作为节点初始嵌入（HD）。
        2.  通过一个前馈网络（FFN1）将高维嵌入降维至更低维度（E）。
        3.  利用图注意力机制，将节点嵌入两两配对，通过另一个前馈网络（FFN2）计算节点对之间的关联强度。
        4.  使用**α-Entmax函数**取代传统的Softmax进行归一化，以生成稀疏的注意力分布，从而抑制不相关节点的噪声信息。
        5.  最后通过一个前馈层（FFN3）生成最终的邻接矩阵（A），该矩阵捕获了由上下文知识驱动的、具有语义意义的空间相关性。

*   **时空图神经网络模块（STGNN Module）**：
    *   **核心思想**：此模块接收上一步生成的**上下文感知的邻接矩阵A**，进行联合时空建模，并输出初步的数值预测。
    *   **关键技术细节**：该框架灵活，可兼容多种STGNN。论文中采用了基于GRU和Graph Diffusion Convolution的经典架构（参考GTS模型）。GRU中的标准矩阵乘法被替换为图上扩散卷积操作，该操作利用邻接矩阵在多步长（S steps）上聚合邻居信息，从而捕捉复杂的空间依赖。

*   **领域知识注入模块（Domain Knowledge Injection Module）**：
    *   **核心思想**：针对STGNN在少样本下输出的初步预测可能不准确的问题，通过**微调一个LLM来校准这些预测**。该LLM被注入领域特定知识、时空上下文和STGNN的初步预测，以进行类似人类的推理和修正。
    *   **关键技术细节**：
        1.  采用监督微调（SFT）和QLoRA技术，高效微调LLaMA-2-7B模型。
        2.  精心设计了**提示（Prompt）**，该提示包含六个关键部分：
            *   **任务指令（Task Instruction）**：描述具体的预测任务。
            *   **节点描述（Node Description）**：来自LLM总结的、节点特定的文本信息。
            *   **节点模式（Node Pattern）**：LLM从少量训练数据中总结出的该节点的模式（如日/周趋势、峰值期）。
            *   **历史输入（Historical Input）**：STGNN所使用的原始数值输入序列。
            *   **数值预测令牌（Numerical Prediction Token）**：STGNN模块输出的初步预测值。
            *   **未来令牌（Future Token）**：仅在训练时提供，作为真实值用于监督学习。
        3.  在推理阶段，微调后的LLM综合所有输入信息，对STGNN的预测令牌进行推理和校正，最终输出更准确、更符合现实约束的预测结果。

### 3. 实验设计

*   **数据集**：使用了两个真实世界多元时间序列数据集来评估少样本预测性能。
    *   **Nottingham（诺丁汉停车场数据集）**：包含19个停车场在15分钟间隔下的可用车位数据。
    *   **ECL（电力消费数据集）**：原始Electricity数据集的子集，包含19个客户每小时的电力消耗（千瓦时）。
*   **少样本场景构建**：为了模拟数据稀缺环境，两个数据集的训练集均被**缩减到仅保留最后一周的数据**，而验证集和测试集保持不变（总数据按70%/10%/20%划分）。
*   **基准方法（Baselines）**：对比了12种主流方法，覆盖面广，包括：
    *   **传统统计模型**：ARIMA、VAR。
    *   **图神经网络模型（STGNNs）**：DCRNN、GraphWaveNet、STSGCN、GMAN、GTS。
    *   **Transformer及线性模型**：PatchTST、iTransformer、DLinear。
    *   **LLM-based模型**：GPT4TS、TimeLLM。
*   **评估指标**：采用时间序列预测领域三个标准指标：**MAE**（平均绝对误差）、**RMSE**（均方根误差）和**MAPE**（平均绝对百分比误差）。

### 4. 资源与算力

*   **硬件配置**：FSTLLM的训练和推理在一台配备 **Intel(R) Core(TM) i7-13700K CPU** 和一块 **NVIDIA A6000 GPU (48GB显存)** 的Linux工作站上进行。
*   **训练细节与优化**：
    *   论文明确指出由于只有单块GPU，无法使用数据并行来加速推理，因此从ECL数据集的321个客户端中选取了19个进行实验，并申明完整数据集在模型上是可训练的，主要是受限于硬件。
    *   模型仅微调 **2个epochs**。
    *   采用**4-bit量化和LoRA（Low-Rank Adaptation）**技术来降低模型显存占用和可训练参数量。LoRA的注意力维度设置为64，初始化学习率为2e-4，使用Adam优化器。

### 5. 实验数量与充分性

*   **主要对比实验**：在两个数据集上，将FSTLLM与12个基线模型在多个预测时间点（Nottingham 8个，ECL 12个）上进行了详尽的性能对比。
    *   **Nottingham**：FSTLLM在24个评估指标（8个预测点 × 3个指标）中取得了22个最佳成绩。
    *   **ECL**：FSTLLM在36个评估指标（12个预测点 × 3个指标）中取得了25个最佳，32个次佳以上的成绩。
*   **消融实验（Ablation Study）**：设计了两个模型变体来验证关键模块的作用：
    1.  **FSTLLM-NoInjection**：移除领域知识注入模块，直接使用STGNN的输出。
    2.  **FSTLLM-NoLLM**：用常见的余弦相似度图学习替换LLM增强的图构建模块，并同时移除领域知识注入模块。
*   **即插即用集成实验（Integration Study）**：为验证框架的灵活性，将框架中的STGNN骨干网络模块替换为**GPT4TS**和**iTransformer**的预测输出，并观察最终性能提升。
*   **数据效率实验**：在Nottingham数据集上，比较了FSTLLM仅用3天训练数据，与其他基线模型分别用3天和30天训练数据的性能。
*   **实验充分性与公平性评价**：实验设计**比较充分且公平**。对比的基线方法多且新，完全覆盖了传统方法、STGNNs、先进Transformer模型和LLM-based模型。消融实验清晰证明了所提两个核心模块的价值。模型集成实验验证了框架的通用性和可扩展性。数据效率实验进一步突显了其在少样本下的核心优势。附录中提供了与更多基线（AGCRN, MTGNN）的完整结果，以及详细的prompt示例，增强了复现性和说服力。

### 6. 论文的主要结论与发现

*   **显著的性能优势**：FSTLLM在少样本时间序列预测任务上，相比所有基线方法均取得了显著且一致的性能提升，特别是在MAPE指标上，在ECL数据集上相对误差降低了超过50%。
*   **关键组件的有效性**：消融实验证明，**领域知识注入模块至关重要**，其移除会导致性能大幅下降；LLM增强的图构建模块也对整体性能有积极贡献。
*   **强大的数据效率和适应性**：FSTLLM仅用3天的训练数据，其性能就**超越了用30天数据训练的多个先进基线模型**，展现了极高的数据效率。
*   **灵活的即插即用性**：FSTLLM可以作为一个增强框架，无缝集成到现有预测模型（如GPT4TS, iTransformer）中，在不修改其架构和参数的情况下，显著提升它们的少样本预测能力。
*   **可解释性和类人推理**：FSTLLM不仅给出预测数值，还能在预测过程中考虑现实世界的约束（如停车场最大容量、用电峰谷规律），从而提供更具可解释性和现实意义的预测。

### 7. 优点

*   **创新型融合**：率先将LLM的上下文知识同时应用于STGNN的**图结构学习**和**预测结果的后校准**，为解决少样本时空预测问题提供了新颖的视角。
*   **可解释性增强**：通过精心设计的prompt和LLM生成的形式，模型在推理时能结合具体情境进行调整（如将预测值限制在停车场最大容量内），相比传统黑盒模型有了质的提升。
*   **框架灵活性高**：FSTLLM不依赖于特定的STGNN架构，其LLM-based的预测校准模块也可以与多种backbone模型集成，具有很强的普适性和扩展价值。
*   **实验扎实全面**：在多个数据集、与大量先进基线进行全面对比，并通过详尽的消融和集成实验，有力地论证了所提框架的有效性和每个模块的价值。

### 8. 不足与局限

*   **硬件限制下的实验规模**：实验受限于单块GPU，ECL数据集仅采用了19个通道的子集。虽然作者论证了模型的可扩展性，但在更大规模（如321个通道）图上的性能和对算力、显存的实际需求仍需验证。
*   **对文本数据的依赖**：LLM增强的图构建模块需要每个时间序列节点都有**对应的、高质量的文本描述**，这在很多实际场景中（如传感器数据）可能无法满足或需要额外成本去构建，限制了其直接应用的广度。
*   **计算与推理成本**：尽管使用了QLoRA等高效微调技术，在推理时仍需通过一个7B级别的LLM进行前向传播，相比仅使用数值模型的方法，**推理延迟和计算成本会更高**，可能不适用于需要毫秒级响应的在线任务。
*   **LLM幻觉风险**：虽然论文展示了LLM能修正预测，但LLM在推理过程中可能产生幻觉或引入文本描述中的偏差，这可能会在某些情况下误校准STGNN的预测，需要更深入的鲁棒性分析。

（完）
