---
title: "Large Language-Geometry Model: When LLM meets Equivariance"
title_zh: 大型语言-几何模型：当LLM遇见等变性
authors: "Zongzhao Li, Jiacheng Cen, Bing Su, Tingyang Xu, Yu Rong, Deli Zhao, Wenbing Huang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Qi9rPcdiTY"
tags: ["query:graph-llm"]
score: 9.0
evidence: 整合几何图神经网络与LLM，在三维物理系统预测中强制E(3)等变性。
tldr: 为解决3D物理系统预测中GNN缺乏外部知识、LLM缺失空间推理的问题，提出EquiLLM框架，通过几何感知提示、等变编码器、LLM及等变适配器，无缝融合E(3)等变GNN与LLM。实验表明，EquiLLM在分子动力学等多个任务上取得最优结果，实现了等变性与语言知识的统一，为几何深度学习与LLM结合提供了新范式。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-qi9rpcdity/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1740, \"height\": 605, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qi9rpcdity/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 830, \"height\": 403, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-qi9rpcdity/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1763, \"height\": 748, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qi9rpcdity/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1144, \"height\": 390, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qi9rpcdity/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1766, \"height\": 490, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qi9rpcdity/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 603, \"height\": 390, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qi9rpcdity/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 852, \"height\": 148, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qi9rpcdity/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1352, \"height\": 414, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qi9rpcdity/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 881, \"height\": 316, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qi9rpcdity/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 819, \"height\": 423, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qi9rpcdity/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 711, \"height\": 118, \"label\": \"Table\"}]"
motivation: 现有方法中，几何GNN缺乏外部知识，LLM难以保证空间等变性。
method: 提出EquiLLM，设计几何提示、等变编码器和适配器，将E(3)等变GNN与LLM深度集成。
result: 在分子动力学等任务上，EquiLLM优于纯GNN和纯LLM方法，预测更准确。
conclusion: 成功实现等变GNN与LLM的无缝结合，为物理系统建模提供新范式。
---

## Abstract
Accurately predicting 3D structures and dynamics of physical systems is crucial in scientific applications. Existing approaches that rely on geometric Graph Neural Networks (GNNs) effectively enforce $\mathrm{E}(3)$-equivariance, but they often fail in leveraging extensive broader information. While direct application of Large Language Models (LLMs) can incorporate external knowledge, they lack the capability for spatial reasoning with guaranteed equivariance. In this paper, we propose EquiLLM, a novel framework for representing 3D physical systems that seamlessly integrates $\mathrm{E}(3)$-equivariance with LLM capabilities. Specifically, EquiLLM comprises four key components: geometry-aware prompting, an equivariant encoder, an LLM, and an equivariant adapter. Essentially, the LLM guided by the instructive prompt serves as a sophisticated invariant feature processor, while 3D directional information is exclusively handled by the equivariant encoder and adapter modules. Experimental results demonstrate that EquiLLM delivers significant improvements over previous methods across molecular dynamics simulation, human motion simulation, and antibody design, highlighting its promising generalizability.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义

- **核心问题**：如何准确预测物理系统的三维结构与动力学（如分子动力学模拟、人体运动预测、抗体设计）是科学计算中的关键挑战。现有两大主流方法各存缺陷：
  - 基于几何图神经网络（GNN）的方法能严格保证 $\mathrm{E}(3)$-等变性，但难以利用大规模外部知识和上下文信息。
  - 大语言模型（LLM）虽可融入丰富领域知识，却缺乏保证空间推理等变性的能力。
- **整体含义**：该文首次提出将LLM与几何GNN深度融合的框架 **EquiLLM**，旨在同时获得等变空间建模能力和LLM广博的常识与知识集成能力，为解决三维物理系统建模提供新范式。

## 2. 论文提出的方法论

EquiLLM由四个核心模块组成，其关键设计在于严格分离**不变信息处理**与**等变方向信息处理**：

- **几何感知提示（Geometry-aware prompting）**  
  为LLM设计任务专属提示，包含三部分：
  - 任务描述（目标与输入输出要求）
  - 对象特征描述（构成与结构特点）
  - 对象统计信息（如原子/关节点到质心的距离统计、基于PCA的降维统计等），确保这些统计在 $\mathrm{E}(3)$ 变换下不变。

- **等变编码器（Equivariant Encoder）**  
  使用任意合适的领域几何GNN（如ESTAG、MEAN）对输入几何图 $\mathcal{G}_{\text{in}}$ 进行编码，输出不变节点特征 $\mathbf{H}'$ 和等变坐标 $\vec{\mathbf{X}}'$。仅将 $\mathbf{H}'$ 经投影层后送入LLM，而 $\vec{\mathbf{X}}'$ 则通过跳跃连接直接传入后续适配器，以维持整体等变性。

- **大语言模型（LLM）**  
  将投影后的不变特征 $\mathbf{H}_{\text{proj}}$ 与提示文本的嵌入按任务特定方式拼接，输入冻结参数的LLM（如GPT-2），提取其输出的不变特征 $\mathbf{H}_{\text{llm}}$。LLM在此充当复杂的不变特征处理器，避免直接处理原始坐标而破坏等变性。

- **等变适配器（Equivariant Adapter）**  
  先将 $\mathbf{H}_{\text{llm}}$ 重新投影并与 $\mathbf{H}'$ 相加得到精炼特征 $\mathbf{H}_r$，再将其与 $\vec{\mathbf{X}}'$ 一起送入单层EGNN进行消息传递与坐标更新，最终生成等变输出坐标 $\vec{\mathbf{X}}_{\text{out}}$ 和不变输出特征 $\mathbf{H}_{\text{out}}$。适配器中的操作均保证平移、旋转、反射下的等变性。

- **整体流程（以动力学预测为例）**  
  $\mathcal{G}_{1:T} \xrightarrow{\text{等变编码器}} (\mathbf{H}',\vec{\mathbf{X}}') \xrightarrow{\text{投影+提示拼接}} \text{LLM} \xrightarrow{\mathbf{H}_{\text{llm}}} \text{等变适配器} \xrightarrow{(\vec{\mathbf{X}}',\mathbf{H}_r)} \mathcal{G}_{T+1:T+F}$  
  loss采用预测坐标与真值的均方误差。

## 3. 实验设计

- **数据集与场景**：
  - **分子动力学模拟**：MD17数据集（8种小分子），输入10帧预测未来10帧坐标。
  - **人体运动模拟**：Human Motion Capture数据集（Walk, Basketball两种动作），预测未来10/15/20帧关节点坐标。
  - **抗体设计**：基于SAbDab构建训练/验证集，RAbD测试集，预测CDR-H3区域的氨基酸序列和三维骨架坐标。

- **对比方法**：
  - 传统GNN、时空GCN。
  - 等变模型：STTFN、ST_SE(3)-Transformer、STEGNN、ESTAG、Equiformer、MEAN、GeoAB。
  - 纯LLM：GPT-4o-mini、Gemini-1.5-flash-latest、DeepSeek-V3（使用相同提示直接输出坐标）。
  - 额外对比：GPT-4o-mini + 坐标规范化（canonicalization）、微调LLaMA（7B）等。

- **评价指标**：均方误差（MSE），以及抗体设计中的氨基酸恢复率（AAR）、TM-score、RMSD。

## 4. 资源与算力

- 文中明确提及所有实验在**单块NVIDIA A100-80G GPU**上完成训练、验证和测试。
- LLM模块（如GPT-2）参数完全冻结，不进行额外训练；等变编码器、适配器等模块从头训练。
- 具体训练时长未详细说明，但给出了统一的超参数配置（学习率、epochs等），整体算力需求处于可接受范围。

## 5. 实验数量与充分性

- **实验组数概览**：
  - MD17：9种以上基线对比（含纯LLM和规范化的LLM），2种统计信息变体（DST、PCA），全面涵盖8种分子。
  - Motion Capture：6种基线在两个子数据集、三种预测长度下共计6组实验。
  - 抗体设计：7种基线方法对比。
  - 消融研究：针对架构（Encoder顺序、LLM移除、适配器缺省）和提示组件（任务描述、对象特征、统计信息）进行多组实验，共十余项消融。
  - 额外探索：微调LLM层、替换非等变编码器、更换更强LLM骨架（Qwen2.5-3B）、微调LLaMA。
- **充分性与公平性**：实验覆盖物理、生物、人体运动三个领域，基线包含SOTA等变GNN和前沿LLM。所有对比均保持统一的超参数、数据划分和评估协议，消融实验系统分析了各组件的贡献，整体实验设计充分且公平。

## 6. 论文的主要结论与发现

- EquiLLM通过将LLM限定为**不变特征处理器**、让几何GNN专门处理**方向相关计算**，成功实现了 $\mathrm{E}(3)$-等变性与LLM知识集成的统一。
- 在分子动力学、人体运动模拟和抗体设计任务上，EquiLLM**全面超越**现有等变GNN模型（如ESTAG、MEAN）以及纯LLM方法（如GPT-4o-mini），取得最优性能。
- 几何提示中的统计信息和对象特征描述对性能提升至关重要；不适当的架构设计（例如LLM直接处理坐标或放在编码器之前）会导致严重性能损失或等变性破坏。
- 冻结LLM参数、仅训练轻量适配器是高效且有效的策略，微调LLM反而可能损害已有知识。

## 7. 优点

- **首创性**：首次系统研究LLM与等变GNN在三维物理系统上的融合，提出了一套完整的、可证明等变的框架。
- **设计原则清晰**：严格分离不变与等变路径，保证了理论等变性又释放了LLM的知识能力。
- **广泛适用性**：在三个不同领域、多种任务和预测长度下均取得显著提升，展示了良好的泛化性。
- **模块化与轻量**：LLM冻结，仅需两个投影层和一个EGNN层，引入的额外参数极少；编码器和LLM可灵活替换。
- **详实的实验与消融**：对比基线全面，消融维度丰富，深入剖析了架构和提示各部分的贡献。

## 8. 不足与局限

- **模型规模限制**：文中LLM主要使用GPT-2（中等规模），虽尝试了Qwen2.5-3B但提升有限；更大规模LLM的效果尚未充分验证，可能受限于文本-3D结构配对数据的匮乏。
- **任务覆盖范围**：当前仅在动力学预测和抗体设计上验证，尚未扩展到其他重要科学任务（如材料性质预测、蛋白质折叠等）。
- **提示设计的依赖性**：几何提示的效果依赖于人工精心构造，自动化或最优提示策略仍有待研究；未探索更复杂的统计特征（如高阶拓扑信息）。
- **理论分析深度**：主要给出了框架的等变性证明，对于LLM具体带来的知识增益机制缺乏深入剖析，解释性有待加强。
- **推理效率**：引入LLM后推理时间有所增加（如在抗体设计任务中，EquiLLM推理时间约为纯GNN方法的2-4倍）。文中仅给出了简单比较，未进行优化的效率分析和部署方案讨论。

（完）
