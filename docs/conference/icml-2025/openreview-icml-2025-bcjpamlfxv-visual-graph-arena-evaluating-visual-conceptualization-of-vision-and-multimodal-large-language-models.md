---
title: "Visual Graph Arena: Evaluating Visual Conceptualization of Vision and Multimodal Large Language Models"
title_zh: 视觉图竞技场：评估视觉和多模态大语言模型的视觉概念化能力
authors: "Zahra Babaiee, Peyman Kiasari, Daniela Rus, Radu Grosu"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=BCJPAmlfxv"
tags: ["query:graph-llm"]
score: 9.0
evidence: 评估多模态大语言模型在图上的视觉推理能力
tldr: 提出视觉图竞技场(VGA)基准数据集，包含六种基于图的视觉推理任务，用于评估多模态大语言模型的视觉抽象与概念化能力；实验表明现有模型与人类表现差距显著，揭示了当前模型在图结构视觉推理上的不足。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1718, \"height\": 404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1673, \"height\": 481, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1646, \"height\": 951, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 565, \"height\": 252, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 334, \"height\": 297, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 386, \"height\": 246, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 843, \"height\": 482, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1418, \"height\": 2031, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1690, \"height\": 878, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1694, \"height\": 877, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1691, \"height\": 876, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1690, \"height\": 875, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1688, \"height\": 874, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1689, \"height\": 877, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1715, \"height\": 609, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1715, \"height\": 608, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1716, \"height\": 608, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1714, \"height\": 610, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1718, \"height\": 608, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1091, \"height\": 1097, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1093, \"height\": 1098, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1095, \"height\": 1097, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1095, \"height\": 1098, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1097, \"height\": 1099, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bcjpamlfxv/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1097, \"height\": 1101, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-bcjpamlfxv/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1504, \"height\": 235, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bcjpamlfxv/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1588, \"height\": 704, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bcjpamlfxv/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 826, \"height\": 317, \"label\": \"Table\"}]"
motivation: 当前多模态大语言模型在视觉问答中缺乏视觉概念化能力，即识别不同视觉形式下的相同概念并推理。
method: 构建包含不同图布局的六种图推理任务基准，以此测试模型的视觉抽象与推理。
result: 实验显示人类近乎完美，而最先进的多模态模型与人类差距明显。
conclusion: VGA揭示了现有模型在图结构视觉推理上的不足，为提升大语言模型的图推理能力提供了方向。
---

## Abstract
Recent advancements in multimodal large language models have driven breakthroughs in visual question answering. Yet, a critical gap persists, `conceptualization'—the ability to recognize and reason about the same concept despite variations in visual form, a basic ability of human reasoning. To address this challenge, we introduce the Visual Graph Arena (VGA), a dataset featuring six graph-based tasks designed to evaluate and improve AI systems’ capacity for visual abstraction. VGA uses diverse graph layouts (e.g., Kamada-Kawai vs. planar) to test reasoning independent of visual form. Experiments with state-of-the-art vision models and multimodal LLMs reveal a striking divide: humans achieved near-perfect accuracy across tasks, while models totally failed on isomorphism detection and showed limited success in path/cycle tasks. We further identify behavioral anomalies suggesting pseudo-intelligent pattern matching rather than genuine understanding. These findings underscore fundamental limitations in current AI models for visual understanding. By isolating the challenge of representation-invariant reasoning, the VGA provides a framework to drive progress toward human-like conceptualization in AI visual models. The Visual Graph Arena is available at: \href{https://vga.csail.mit.edu/}{vga.csail.mit.edu}.

---

## 论文详细总结（自动生成）

### 一、论文的核心问题与整体含义
- **研究动机**：当前多模态大语言模型在视觉问答领域取得突破，但缺乏一项人类推理的基本能力——**视觉概念化**，即在不同视觉形式（如图的布局变化）下，依然能识别并推理出相同的抽象概念。
- **核心问题**：现有模型是否具备**表示不变的图结构视觉推理能力**？即，当同一张图以不同布局（如能量布局与平面布局）呈现时，模型能否正确回答相关推理问题（如同构判断、找路径、找环等）。
- **整体含义**：通过构建基准数据集 `Visual Graph Arena (VGA)`，系统揭示当前最先进多模态模型在图概念化上的致命短板，为通向人类层面的视觉抽象提供评测框架和洞察。

### 二、论文提出的方法论
- **核心思想**：以“图”为概念载体，通过变化其**视觉布局**（如 `Kamada-Kawai` vs. 平面布局）但仍保持相同的图结构，来孤立测试模型的**概念抽象与表示不变推理**能力。
- **关键技术细节**：
  - 设计了一套包含 **六种图推理任务** 的基准数据集，涵盖：同构检测、路径查找、环查找等（具体全六种任务摘要未详尽列出，但从结果反推包括同构、路径、环相关的若干任务）。
  - 每个问题都对应不同布局的同一图结构，迫使模型必须穿透视觉表象、捕捉结构化关系，而非依赖视觉纹理。
  - 本质上是一个评测框架，未涉及新模型结构或公式；其技术含量体现在任务构造、布局生成以及对“概念化”能力的精准定义与度量。

### 三、实验设计
- **数据集/场景**：`Visual Graph Arena (VGA)` 数据集，利用多种图布局构建问答对。
- **基准（Benchmark）**：以**人类表现**为黄金标准；人类在同一批任务中取得了近乎完美的准确率。
- **对比方法**：广泛评估了**当前最先进的视觉模型与多模态大语言模型**（摘要未逐一列举具体模型名称，仅用 `state-of-the-art vision models and multimodal LLMs` 概括，可能包括 GPT-4V、Gemini-Vision、LLaVA 等代表性系统）。

### 四、资源与算力
- **算力使用情况**：**文中未明确说明**。由于该工作主要贡献是基准数据集的构建与评估，不涉及大规模模型训练，所使用的算力（如评估所用 GPU）未被提及。如果需要实际复现评估，仅需常规推理算力，无特殊运算需求报告。

### 五、实验数量与充分性
- **实验组数**：至少包含六种不同的图推理任务；每种任务下又涵盖多种图布局的变体；同时对比了人类和最先进的多种多模态模型。
- **充分性与公平性**：从摘要结论（模型在同构检测上彻底失败，伪智能行为）来看，实验设计**足够揭示关键缺陷**。但因缺少具体模型名称、样本量、统计检验等细节，无法完全判断样本规模是否足够大、所选基线是否覆盖最应测评的模型。整体设计边界清晰、对比方法合理（以人类为标杆），具有较好的客观性与公平性。

### 六、论文的主要结论与发现
- **人类 vs. 模型的巨大鸿沟**：人类几乎在所有任务上表现完美，而最先进的视觉或多模态大模型则遇到严重困难。
- **特定任务上的极端失败**：模型在**同构检测（isomorphism detection）**上完全失败，在**路径/环相关任务**上仅取得有限成功。
- **推理行为异常**：模型表现出**伪智能模式匹配**的特征，类似于表面视觉模式的抓取，而非真正的逻辑理解和结构推理。
- **根本局限**：当前 AI 模型在需要脱离视觉形式、进行抽象概念推理时存在根本性不足。

### 七、优点
- **洞察深刻**：精准定义了“视觉概念化”并给出可操作的测评手段，直指多模态模型的本质弱点。
- **任务设计巧妙**：通过改变布局来分离视觉外观与结构概念，有效排除了模型依赖纹理或位置捷径的可能。
- **基准标杆强**：以近乎完美的人类表现作为对照，使得模型的能力缺陷被定量且醒目地暴露出来。
- **方向指引明确**：为提升大语言模型的图结构推理和抽象理解能力提供了清晰的挑战集和未来研究框架。

### 八、不足与局限
- **实验覆盖透明度不足**：摘要及提供的元数据**未详细列出被测模型的具体名称、版本、规模**，也未公布数据集的样本总量和任务细节，限制了可复现性与细致评判。
- **任务范围局限**：整体集中在图结构的视觉推理，尚未拓展到其他类型的视觉抽象（如符号、几何变换、抽象画等），其结论的泛化边界有待拓宽。
- **缺乏解决方案**：仅诊断了问题，没有给出改进模型性能的具体方法或训练策略。
- **潜在偏差风险**：未知图生成的参数分布是否覆盖了真实场景的变化，可能存在布局偏好；此外，人类表现可能基于少量样本，若无详细实验统计则存在高估风险。
- **应用限制**：作为一个测评基准，它不直接产生更强的模型，无法单独提升实际应用系统的能力，其价值更多体现在诊断和方向引导上。

（完）
