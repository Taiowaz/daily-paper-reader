---
title: Compile Scene Graphs with Reinforcement Learning
title_zh: 使用强化学习编译场景图
authors: "Zuyao Chen, Jinlin Wu, Zhen Lei, Marc Pollefeys, Chang Wen Chen"
date: 2025-04-18
pdf: "https://openreview.net/pdf?id=Wf3EbtqGdw"
tags: ["query:graph-llm"]
score: 8.0
evidence: 训练多模态大语言模型端到端生成场景图这一图结构表示
tldr: 针对大语言模型端到端提取结构化视觉表示（如场景图）的探索不足，提出通过监督微调和强化学习训练多模态大语言模型，使其能直接生成场景图三元组，实验证明该方法在场景图生成任务上表现优异，拓展了LLM在结构预测任务上的能力。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-wf3ebtqgdw/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1245, \"height\": 648, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wf3ebtqgdw/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1434, \"height\": 895, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wf3ebtqgdw/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1409, \"height\": 1990, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wf3ebtqgdw/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1413, \"height\": 2015, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wf3ebtqgdw/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1432, \"height\": 1400, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wf3ebtqgdw/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1394, \"height\": 2133, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wf3ebtqgdw/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1345, \"height\": 2062, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-wf3ebtqgdw/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1158, \"height\": 726, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wf3ebtqgdw/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1161, \"height\": 741, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wf3ebtqgdw/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1238, \"height\": 160, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wf3ebtqgdw/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1442, \"height\": 454, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wf3ebtqgdw/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1455, \"height\": 446, \"label\": \"Table\"}]"
motivation: 现有LLM主要用于文本生成，端到端提取结构化图表示（如场景图）的研究不足。
method: 通过SFT和RL训练多模态LLM，使其以三元组形式直接输出场景图。
result: 在场景图生成数据集上达到先进性能，并具备零样本能力。
conclusion: LLM可有效地用于生成结构化图，为视觉理解提供了新途径。
---

## Abstract
Next token prediction is the fundamental principle for training large language models (LLMs), 
and reinforcement learning (RL) further enhances their reasoning performance.
As an effective way to model language, image, video, and other modalities, 
the use of LLMs for end-to-end extraction of structured visual representations, such as scene graphs, remains underexplored.
It requires the model to accurately produce a set of objects and relationship triplets, rather than generating text token by token.
To achieve this, 
we introduce  R1-SGG, 
a multimodal LLM (M-LLM) initially trained via supervised fine-tuning (SFT) on the scene graph dataset and subsequently refined using reinforcement learning  to enhance its ability to generate scene graphs in an end-to-end manner.
The SFT follows a conventional prompt-response paradigm, 
while RL requires the design of effective reward signals. 
We design a set of graph centric rewards, including three recall based variants—Hard Recall, Hard Recall+Relax, and Soft Recall—which evaluate semantic and spatial alignment between predictions and ground truth at the object and relation levels.
A format consistency reward further ensures that outputs follow the expected structural schema.
Extensive experiments on the VG150 and PSG benchmarks show that R1-SGG substantially reduces failure rates and achieves strong performance in Recall and mean Recall, surpassing traditional SGG models and existing multimodal language models.

---

## 论文详细总结（自动生成）

好的，以下是根据您提供的论文内容生成的结构化、深入、客观的中文总结。

### 1. 论文的核心问题与整体含义

*   **研究动机**：
    *   场景图作为一种结构化的视觉表征，在机器人、医学图像分析等领域有广泛应用。
    *   传统的场景图生成（SGG）模型通常将任务解耦为目标检测和关系识别，容易过拟合到标注数据集的分布，产生偏向头部长尾分布的关系预测（如“on”、“of”）。
    *   近期方法试图利用大语言模型（LLM）或多模态大语言模型（M-LLM）从文本描述或图像直接生成场景图，但面临指令遵循能力差、生成结果不准确、格式混乱（如重复响应、位置不准）等问题。
*   **核心问题**：
    *   如何有效地利用和训练多模态大语言模型，使其能够端到端地生成准确、完整且结构有效的场景图。
*   **整体含义**：
    *   本研究旨在探索一种新范式，不仅仅将LLM用于文本生成，而是通过结合监督微调（SFT）和强化学习（RL），使M-LLM能够胜任复杂的结构化视觉预测任务（即场景图生成）。

### 2. 论文提出的方法论

*   **核心思想**：
    *   提出 **R1-SGG** 框架，通过两个阶段训练M-LLM进行端到端的场景图生成。
    *   第一阶段：采用传统的**监督微调**，使用`提示-响应`对让模型初步学会生成结构化的场景图格式。
    *   第二阶段：采用**强化学习**（特别是GRPO算法），通过设计一套以图结构为核心的**奖励函数**来精细优化模型，克服SFT在纠正结构性错误方面的不足。
*   **关键技术细节**：
    *   **基础模型**：使用现成的多模态大语言模型（如 Qwen2-VL）。
    *   **强化学习算法**：采用**组相对策略优化 (GRPO)**。GRPO通过比较同一输入下生成的一组候选输出的奖励来计算优势函数，稳定策略更新，无需额外的批评家（Critic）网络。
    *   **奖励函数设计**：设计了多层次的、基于规则的奖励信号，包括：
        1.  **格式奖励**：确保模型输出符合 `<think>...</think><answer>...</answer>` 格式。
        2.  **场景图奖励**：包含三种变体，用于评估预测与真实值的对齐程度。
            *   **硬召回**：严格要求三元组的主语、谓语、宾语标签完全匹配，且边界框IoU > 0.5，与标准评估指标对齐，但奖励稀疏。
            *   **硬召回+松弛**：在硬召回基础上，用标签的嵌入相似度代替完全匹配，增加奖励密度。
            *   **软召回**：将匹配形式化为二分图匹配问题，结合标签相似度、IoU和框距离构建匹配代价，提供更密集的奖励信号。

### 3. 实验设计

*   **数据集与场景**：
    *   **VG150**：广泛使用的场景图数据集，包含150个物体类别和50个关系类别。训练集56,224对，验证集5,000对。
    *   **PSG**：基于COCO的全景场景图数据集，包含80个物体、53个背景类别和56个关系类别。训练集46,563对，测试集2,186对。
*   **基准（Benchmark）与评估**：
    *   **任务协议**：主要采用无预设框的 **SGDET** 协议。
    *   **评估指标**：
        *   **Recall** 和 **平均Recall (mRecall)**：评估三元组的召回率。
        *   **AP@50**：评估目标检测性能。
        *   **失败率**：评估模型输出格式不正确的比例。
*   **对比方法**：
    *   **特定模型**：如 IMP, MOTIFS, VCTree, OvSGTR。
    *   **商业 M-LLMs**：如 GPT-4o, Gemini 系列（1.5 Flash, 2.0 Flash）。
    *   **开源 M-LLMs**：如 LLaVA v1.5, Qwen2-VL。
    *   **模型自身变体**：进行了SFT、RL (R1-SGG-Zero) 和 SFT+RL (R1-SGG) 的消融对比。

### 4. 资源与算力

*   **SFT训练**：在 **4 x NVIDIA A100 (80GB)** GPU上训练3个epoch，批大小为128。
*   **RL训练**：在 **16 x NVIDIA GH200 (120GB)** GPU上训练1个epoch，批大小为32，每个样本生成8个候选输出。
*   **优化器**：均使用AdamW，SFT最大学习率1e-5，RL最大学习率6e-7。
*   **加速库**：使用 **vLLM** 加速RL阶段的采样过程，代码基于 **trl** 库。

### 5. 实验数量与充分性

*   **实验数量**：实验设计较为全面，主要包括：
    1.  **主实验**：在VG150和PSG两个数据集上，对比了2B和7B两种模型规模下，零样本、SFT、RL和SFT+RL的性能。
    2.  **跨数据集泛化实验**：评估在VG150上训练的模型在PSG上的表现，反之亦然。
    3.  **消融实验**：探讨了奖励函数变体（硬召回 vs. 软召回）、KL正则化、采样长度、分组大小等关键因素的影响。
    4.  **定性分析**：可视化展示了不同训练阶段模型生成的场景图。
    5.  **辅助分析**：通过一个四选一的视觉问答任务，评估了现有M-LLM的基础视觉关系推理能力。
*   **充分性与客观性**：
    *   **充分性**：实验覆盖了多个主流数据集、多种模型规模和多种训练策略，并进行了一系列消融研究来验证核心组件（如奖励设计）的有效性，实验设计相对充分。
    *   **客观性与公平性**：对比了传统特定模型、商业和开源M-LLM等多个强基线，评估标准遵循领域公认的SGDET协议，具备客观公平性。不足之处在于未报告结果的误差线或统计显著性检验。

### 6. 论文的主要结论与发现

*   **RL优于SFT**：仅使用SFT的M-LLM仍存在较高的格式失败率，而RL（GRPO）能极大降低失败率，并能显著提升召回率和平均召回率。
*   **SFT为RL提供良好初始化**：在SFT模型基础上进行RL训练（即R1-SGG），其性能优于直接进行RL训练（即R1-SGG-Zero），尤其在领域内数据集上。
*   **奖励稀疏性设计的重要性**：与直觉相反，与评估指标严格对齐的稀疏奖励（硬召回）比密集的松弛奖励（软召回）带来了更好的最终性能。
*   **长尾预测能力**：相比传统模型和SFT基线，R1-SGG生成了更少偏差的场景图，在尾部关系类别上取得了更高的召回率。
*   **M-LLM的SGG可行性**：证明了通过合理的训练范式，M-LLM能在结构化预测任务（如SGG）上取得超越传统特定模型的性能。

### 7. 优点：方法或实验设计上的亮点

*   **新颖的训练范式**：开创性地将GRPO强化学习应用于多模态LLM的端到端场景图生成任务，为解决LLM的结构化输出难题提供了有效思路。
*   **精巧的奖励设计**：针对场景图的图结构特性，设计了多层次的、从稀疏到密集的奖励函数系列，并深入分析了不同奖励特性对策略优化的影响，为相关任务提供了有价值的参考。
*   **全面的实验分析**：实验设计系统而深入，不仅包含与多类基线的性能对比，还涵盖了跨数据集泛化、多维度消融研究和定性可视化，对方法的有效性提供了强有力的证据。
*   **实用的工程实现**：公开了技术细节（如提示模板、超参数）并应用了vLLM等加速工具，提升了工作的可复现性和实用性。

### 8. 不足与局限

*   **奖励工程依赖**：奖励函数基于规则设计（如对类别标签的依赖），这可能限制了其在开放词汇场景下的应用灵活性，尽管论文评估了“w/o cats.”的设置，但仍依赖既定的评估标准。
*   **计算资源需求高**：RL训练阶段需要16块高端GPU (GH200)，这对于资源有限的研究者来说复现成本较高。
*   **数据集规模与泛化性**：实验主要在VG150和PSG两个数据集上进行，场景图的复杂度和规模依然有限。模型在更真实、更多样化的场景中的鲁棒性尚未得到验证。
*   **忽略CoT推理**：论文观察到模型难以自发产生 Chain-of-Thought 推理，暗示纯粹的规则奖励可能不足以激发深层推理能力，但未对此进行深入解决。
*   **缺少统计分析**：实验结果未报告误差棒、方差或统计显著性检验，无法完全排除结果的随机性影响。

（完）
