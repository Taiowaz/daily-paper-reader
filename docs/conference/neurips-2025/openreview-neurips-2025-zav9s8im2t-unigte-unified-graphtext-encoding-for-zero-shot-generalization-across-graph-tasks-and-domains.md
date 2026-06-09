---
title: "UniGTE: Unified Graph–Text Encoding for Zero-Shot Generalization across Graph Tasks and Domains"
title_zh: "UniGTE: 统一图文本编码实现跨图任务和领域的零样本泛化"
authors: "Duo Wang, Yuan Zuo, Guangyue Lu, Junjie Wu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=zaV9s8iM2T"
tags: ["query:graph-llm"]
score: 10.0
evidence: 用图文本注意力增强LLM，实现统一的结构与语义推理
tldr: 传统图神经网络受限于固定标签空间，大语言模型难以捕捉图结构。本文提出UniGTE框架，在自回归LLM中添加可学习的对齐令牌和结构感知的图文本注意力机制，实现联合编码图结构和自然语言任务描述。在多个未见过的图任务和领域上，UniGTE取得显著的零样本泛化效果，统一了结构与语义推理。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-zav9s8im2t/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1427, \"height\": 632, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zav9s8im2t/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1267, \"height\": 422, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-zav9s8im2t/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1302, \"height\": 383, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zav9s8im2t/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1020, \"height\": 365, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zav9s8im2t/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1173, \"height\": 748, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zav9s8im2t/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1120, \"height\": 517, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zav9s8im2t/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1411, \"height\": 1614, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zav9s8im2t/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1440, \"height\": 289, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zav9s8im2t/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1448, \"height\": 239, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zav9s8im2t/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1132, \"height\": 296, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zav9s8im2t/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1447, \"height\": 239, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zav9s8im2t/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1448, \"height\": 243, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zav9s8im2t/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1445, \"height\": 243, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zav9s8im2t/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1444, \"height\": 243, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zav9s8im2t/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1445, \"height\": 271, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zav9s8im2t/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1449, \"height\": 199, \"label\": \"Table\"}]"
motivation: GNN受固定标签空间限制，LLM难以捕获图结构信息。
method: 提出UniGTE，在LLM中加入对齐令牌和图文本注意力，联合编码图与文本。
result: 在多个未见图任务和领域上实现强零样本泛化。
conclusion: UniGTE为图与语言模型的深度融合开辟了新方向。
---

## Abstract
Generalizing to unseen graph tasks without task-specific supervision is challenging: conventional graph neural networks are typically tied to a fixed label space, while large language models (LLMs) struggle to capture graph structure. We introduce UniGTE, an instruction-tuned encoder–decoder framework that unifies structural and semantic reasoning. The encoder augments a pretrained autoregressive LLM with learnable alignment tokens and a structure-aware graph–text attention mechanism, enabling it to attend jointly to a tokenized graph and a natural-language task prompt while remaining permutation-invariant to node order. This yields compact, task-aware graph representations. Conditioned solely on these representations, a frozen LLM decoder predicts and reconstructs: it outputs the task answer and simultaneously paraphrases the input graph in natural language. The reconstruction objective regularizes the encoder to preserve structural cues. UniGTE is instruction-tuned on five datasets spanning node-, edge-, and graph-level tasks across diverse domains, yet requires no fine-tuning at inference. It achieves new state-of-the-art zero-shot results on node classification, link prediction, graph classification and graph regression under cross-task and cross-domain settings, demonstrating that tight integration of graph structure with LLM semantics enables robust, transferable graph reasoning.

---

## 论文详细总结（自动生成）

好的，请查收以下基于论文《UniGTE: Unified Graph–Text Encoding for Zero-Shot Generalization across Graph Tasks and Domains》的结构化中文总结。

### **1. 论文的核心问题与整体含义**
*   **研究动机与背景**: 零样本图学习面临两大挑战：一是图神经网络 (GNN) 在零样本场景下泛化能力弱，因其输出头与特定任务和标签空间绑定，难以适应新任务；二是大型语言模型 (LLM) 虽然具备强大的零样本推理潜力，但直接处理序列化的图数据效果不佳，因为它缺乏对图结构固有的归纳偏置。
*   **核心问题**: 如何构建一个能跨越不同图任务（节点、边、图级别）和不同领域，且无需任何微调即可实现强零样本泛化的统一模型。
*   **整体含义**: 本文提出 UniGTE，旨在通过一个统一的编码器-解码器框架，将图的结构化推理与 LLM 的语义推理进行深度融合，从而实现可迁移、鲁棒的图推理能力。

### **2. 论文提出的方法论**
*   **核心思想**: UniGTE 采用“LLM编码器 + 冻结LLM解码器”的框架。其核心在于让 LLM 编码器在习得图结构的**同时**，结合自然语言任务描述，生成一个紧凑的、包含任务信息的图表示，用以指导冻结的 LLM 解码器生成最终答案。
*   **关键技术细节**:
    *   **统一图-文编码器**:
        *   **输入构造**: 对于节点/边级任务，围绕目标节点/边采样 k-跳子图，所有节点作为输入 token。输入序列由三部分拼接而成：图节点 Token (`T_G`)、任务描述 Token (`T_desc`) 和一组固定大小的、可学习的**对齐 Token (`A`)**。
        *   **结构感知的图-文注意力机制**: 这是一个关键创新，旨在保持节点排列不变性的同时注入结构信息。
            *   **跨模态 RoPE**: 为图 token 分配一个共享的、可学习的位置索引，使得任意两节点间的相对距离为 0，以此实现排列不变性。对于图 token 与文本 token 的交互，则计算其位置偏移。
            *   **加性偏置**: 在注意力分数上增加三项偏置来显式编码结构信息：
                1.  **距离偏置 (`b^{PE}_{ij}`)**: 基于图节点间最短路径距离的可学习查找表。
                2.  **边感知偏置 (`b^{Edge}_{ij}`)**: 对最短路径上的所有边，用一个 MLP 编码其自然语言描述并聚合。
                3.  **掩码偏置 (`b^M_{ij}`)**: 控制注意力流向。图 token 之间、图 token 对文本 token 可双向注意力，但文本 token 不能注意图 token，以防止信息泄露。
    *   **解码与训练**:
        *   **任务感知的图表征**: 编码器最后一层在对齐 Token `A` 上的隐藏状态 `H_A` 被提取出来，作为融合了结构和任务信息的紧凑图表征，这是解码器唯一的条件信号。
        *   **双重目标**: 冻结的 LLM 解码器基于 `H_A` 和任务细节指令 `T_detail` 进行自回归生成，同时优化两个目标：
            1.  **指令微调损失 (`L_{IT}`)**: 准确生成任务答案。
            2.  **辅助重构损失 (`L_{prompt}`)**: 重构输入的图描述文本。该目标正则化编码器，强制其在 `H_A` 中保留图的结构线索。
        *   **参数高效微调**: 训练时解码器完全冻结，仅更新编码器中的少量参数：LoRA适配器、对齐 Token 嵌入、边偏置 MLP 和距离偏置查找表。

### **3. 实验设计**
*   **训练数据集**: 5个数据集，覆盖多任务和多领域。
    *   **节点分类**: Arxiv (引文网络), Children (电商), Computer (电商)
    *   **链接预测**: FB15K237 (知识图谱), Arxiv/Children/Computer (对应数据集上构建)
    *   **图分类**: ChEMBL (分子图)
*   **评估设置与基准(零样本)**:
    *   **域内 (In-domain)**: 在与训练集同域的未见数据集上评估，如 Pubmed/Cora (引文)、Photo/Sports (电商)、HIV/BACE/PCBA (分子)。
    *   **跨域 (Cross-domain)**: 在全新领域评估，如 WikiCS (网络链接)、Reddit/Instagram (社交网络)。
    *   **跨任务 (Cross-task)**: 在未见任务上评估，如图回归任务，使用 Esol, Lipo, Freesolv 数据集。
*   **对比方法**:
    *   **纯LLM基线**: Vicuna-7B (未经过图训练)。
    *   **GNN预测器 + LLM增强**: OFA。
    *   **LLM预测器**:
        *   **松散耦合**: GraphGPT, LLaGA, TEA-GLM (通过投影层对齐 GNN 和 LLM)。
        *   **紧密耦合**: GOFA (在 LLM transformer 层间插入 GNN 层)。

### **4. 资源与算力**
*   论文明确指出，所有实验均在配备**两块 NVIDIA A100 GPU (每块 80GB 显存)** 的机器上进行。
*   论文未提供具体的总训练时长。

### **5. 实验数量与充分性**
*   **实验数量**: 作者设计了较为全面的实验组合。
    *   **主要实验**: 涵盖 3 种泛化场景（域内、跨域、跨任务）下的 4 类图任务（节点分类、链接预测、图分类、图回归），涉及约 15 个评估数据集。
    *   **消融实验**: 验证对齐Token (`w/o AT`) 和任务感知图编码 (`w/o TA`) 两个核心组件的有效性，并从领域和任务两个视角进行分析。
    *   **辅助分析**: 包含合法性测试（衡量模型生成有效响应比例）和计算效率对比（与GOFA和纯LLM对比推理时间和性能）。
*   **充分性与公平性**:
    *   **充分性**: 实验覆盖了多种任务和领域，很好地支撑了模型能在不同复杂度下进行零样本泛化的论点。
    *   **客观公平性**: 论文作者称对于大多数基线方法，均**重新运行了官方代码**并在其实验设置下进行评估。对于 GraphGPT，由于计算成本高，直接引用了原论文数据；GOFA 则使用官方预训练检查点进行指令微调。这些处理相对公平，但不同模型的初始预训练强度不同，可能仍会带来细微影响。未汇报误差条，理由是 LLM 训练成本过高。

### **6. 论文的主要结论与发现**
*   UniGTE 在所有评估数据集和零样本设置下，**一致地取得了最优结果**，显著超越现有基线模型。
*   **对齐 Token 和任务感知编码至关重要**: 消融实验证明，移除任一组件都会导致性能大幅下降，验证了它们在融合多模态信息和提供细粒度任务信号方面的核心作用。
*   **结构-语义紧密整合的优势**: 实验结果表明，相比将 GNN 和 LLM 松散耦合（如 TEA-GLM）或仅进行后期注入（如 GOFA）的方法，UniGTE 通过统一的注意力机制在编码阶段就深度融合图结构与任务语义，能实现更鲁棒、更可迁移的图推理。
*   UniGTE 在保持强大零样本性能的同时，推理速度比同类型模型（GOFA）和纯 LLM（Vicuna-7B）更快，展现出计算效率优势。

### **7. 优点**
*   **方法创新性强**: 提出的结构感知图-文注意力机制，通过组合跨模态RoPE和多重加性偏置，优雅地解决了图数据的排列不变性和结构编码问题，是网络架构层面的重要贡献。
*   **统一框架设计精妙**: 使用可学习的对齐Token作为图模态与文本模态的桥梁和信息瓶颈，不仅统一了表示空间，还压缩了序列长度，提升了效率。结合任务预测与图重构的双重目标，提供了密集的训练信号。
*   **实验设计周全**: 零样本评估体系设计得非常详尽，从域内、跨域到跨任务逐步递进，全面验证了模型的泛化边界。与多种类型的 SOTA 基线进行了广泛对比，结论可靠。
*   **性能与效率兼备**: 在取得最优性能的同时，模型推理速度更快，展示了其设计的实用性。

### **8. 不足与局限**
*   **链接预测性能增益有限**: 作者在局限性部分承认，UniGTE 在链接预测任务上的提升不如节点分类和图回归显著，并指出这与链接预测的成对特性和提示构建的挑战有关。
*   **训练开销与资源需求**: 虽然推理时效率高，但训练过程涉及对包含 LLM 的大规模模型进行微调，硬件门槛极高（需要 2x 80GB A100），这限制了其可复现性。
*   **未报告误差条**: 出于计算成本考量，作者未进行多次运行以报告标准差，难以评估结果的统计显著性和稳定性。
*   **未见任务类型的泛化**: 论文评估了分类和回归任务，但对其他图任务（如图生成、异常检测）的零样本能力未知。

（完）
