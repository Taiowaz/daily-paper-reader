---
title: "On the Bias of Next-Token Predictors Toward Systematically Inefficient Reasoning: A Shortest-Path Case Study"
title_zh: 论下一个令牌预测器对系统低效推理的偏差：以最短路径为例
authors: "Riccardo Alberghi, Elizaveta Demyanenko, Luca Biggio, Luca Saglietti"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=l8razJItEy"
tags: ["query:graph-llm"]
score: 8.0
evidence: 通过分层图上的最短路径任务研究LLM推理偏差以分析系统性推理
tldr: 为探究大语言模型在图推理任务中的系统性偏差，该研究在分层图最短路径任务上进行控制实验，比较使用最优自底向上动态规划轨迹与长而次优轨迹训练的解码器仅变换器模型。结果表明，最优轨迹训练的模型推理更系统高效，揭示了结构化思维链对于图推理的价值，为提升 LLM 图推理能力提供了实证依据。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1387, \"height\": 708, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1167, \"height\": 597, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1373, \"height\": 479, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1393, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1175, \"height\": 442, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1178, \"height\": 515, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1398, \"height\": 888, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 953, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 567, \"height\": 750, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l8razjitey/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 919, \"height\": 444, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-l8razjitey/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1449, \"height\": 1425, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l8razjitey/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1315, \"height\": 195, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l8razjitey/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1343, \"height\": 152, \"label\": \"Table\"}]"
motivation: LLM 在图推理中如何分配推理计算并避免冗余，以及系统性推理为何有效仍不清晰。
method: 通过分层图最短路径任务训练仅解码器变换器，对比最优动态规划轨迹与长次优轨迹下的推理行为。
result: 使用最优自底向上 DP 轨迹训练的模型推理更准确高效，避免了长轨迹中的冗余与偏差。
conclusion: 系统且增量的推理模式能显著提升 LLM 在图问题上的推理质量，为未来推理策略设计提供指导。
---

## Abstract
Recent advances in natural language processing highlight two key factors for improving reasoning in large language models (LLMs): (i) allocating more test-time compute tends to help on harder problems but often introduces redundancy in the reasoning trace, and (ii) compute is most effective when reasoning is systematic and incremental, forming structured chains of thought (CoTs) akin to human problem-solving. To study these factors in isolation, we introduce a controlled setting based on shortest-path tasks in layered graphs. We train decoder-only transformers on question–trace–answer triples using a custom tokenizer, comparing models trained on optimal bottom-up dynamic programming traces with those trained on longer, valid traces involving backtracking. Surprisingly, under the same training-token budget, the latter models generalize better to unseen graphs. This benefit is not due to length alone—injecting arbitrary redundancy into reasoning traces fails to help and can even hurt performance. Instead, we find that generalization correlates with the model's confidence in next-token prediction, suggesting that long, coherent, and locally incremental traces make the training signal easier to optimize.

---

## 论文详细总结（自动生成）

好的，以下是根据论文内容生成的结构化中文总结。

## 1. 论文的核心问题与整体含义
- **研究动机**：现代大语言模型（LLM）在推理任务上取得突破，但关键机制尚不明确。研究表明，增加测试时计算（更长思维链）有助于解决难题，但往往引入冗余；而系统性、渐进式的推理（如动态规划）被认为更有效。
- **核心问题**：论文试图在受控环境中探究：
  - 模型能否不经中间步骤直接学习最优路径？
  - 思维链（CoT）是否简化任务？
  - 最优的动态规划策略是否是最佳的训练 CoT 选择？
  - 何时增加 CoT 步骤是有益的？
  - 不同解答策略的结构是否对下一个令牌预测有不同适用性？
- **整体含义**：揭示下一个令牌预测架构（transformers）存在一种归纳偏好：相较于全局最优的短推理链，模型更易学习系统性的、局部增量的、即使更长（低效）的推理轨迹。这暗示“教模型什么最合理”与“模型最容易学什么”并不一致。

## 2. 论文提出的方法论
- **任务设计**：在分层有向无环图（DAG）上求解最短路径问题，参数为 `{L, K, C, pe}`，分别表示最大层数、每层最大节点数、最大边代价、平均连接概率。输入为图的符号化序列（问题），输出为最短路径（答案）。
- **推理轨迹生成**：通过一个可调参数的探索算法生成推理轨迹。温度参数 **η** 控制探索顺序：
  - **η = +5**：层优先（DP 型），生成自底向上的最优动态规划轨迹，步骤最少。
  - **η = 0**：均匀随机选择路径，引入一些回溯。
  - **η = −5**：深度优先搜索（DFS 型），需要大量回溯，轨迹更长。
  - 冗余变体：**η = +5 (DR)**（每个步骤确定性地重复一次）和 **η = +5 (RR)**（步骤完成后以 0.5 概率重新加入队列），以人为增加长度。
- **模型与训练**：从头训练一个解码器仅有的 transformer（Phi3 架构，3 层，12 注意力头，隐藏维度 768，28.5M 参数）。在问题-轨迹-答案三元组上进行下一个令牌预测任务，损失仅计算在轨迹和答案部分，屏蔽问题部分。
- **评估指标**：
  - **答案准确率**：路径可行性、层数正确、代价最小且一致。
  - **思维链步骤数**：格式正确的部分路径声明数量。
  - **下一个令牌置信度**：生成轨迹中每个令牌的平均采样概率。

## 3. 实验设计
- **数据集**：合成生成的唯一图实例，训练和测试集不相交。固定图参数 `{L=7, K=6, C=5, pe=0.6}`，根据令牌预算生成不同规模的训练语料（如 32M、128M 令牌）。
- **对比方法（消融条件）**：
  - 无 CoT 基线：直接问题-答案训练。
  - 不同效率的 CoT：`η = +5`, `η = 0`, `η = −5`。
  - 冗余 CoT：`η = +5 (DR)`, `η = +5 (RR)`。
  - 不同训练令牌预算：32M vs 128M，以及按相同图例数量训练对比。
  - 不同采样温度：在推理时尝试非零温度。
- **主要评估场景**：在未见过的同分布图上测试泛化能力。

## 4. 资源与算力
- **硬件**：大部分训练运行在 Nvidia A100 (80GB) 或 RTX4090 (24GB) GPU 上，搭配 32 CPU 核心。
- **训练配置**：批大小固定为 16384 个非填充令牌，学习率恒定 2e-5，使用 AdamW 优化器。不同实验的训练时长由测试损失平稳后终止决定，未给出具体训练总时长或 GPU 小时数。
- **模型大小**：28.5M 参数，3 层 transformer，内存占用约 14GB GPU 内存（FP16）。

## 5. 实验数量与充分性
- **实验数量**：
  - 图 3：展示无 CoT vs 有 CoT（η=+5）在不同图深度下的表现，并分析了中间子任务的学习动态。
  - 图 4：比较 η=+5, 0, -5 三种条件，在 32M 与 128M 令牌预算下的准确率、置信度和训练损失。
  - 图 5/图 6：比较冗余轨迹（DR/RR）及非零温度的影响。
  - 附录中包含不同模型规模（3 层 vs 6 层）、不同令牌预算（16M vs 32M）以及 CoT 质量指标的额外实验。
- **充分性与客观性**：每个实验通常运行 5 个随机种子，并以 1σ 误差棒表示；测试集为 10000 个未见图。对比条件控制了令牌预算或样本数量，且分析了冗余、结构、置信度等多个维度。实验设计系统、细致，能较好支持核心主张。

## 6. 论文的主要结论与发现
- **CoT 至关重要**：模型直接从问题到答案无法在深层图上泛化，但给出结构化思维链后性能显著提升。
- **结构比全局最优性更重要**：在相同训练令牌预算下，用更长、系统低效的 DFS 轨迹（η=−5）训练的模型比用全局最优 DP 轨迹（η=+5）训练的模型泛化得更好，即使因此看到更少的独特图。
- **单纯增加长度无益**：人为注入冗余（η=+5 DR/RR）并不能带来相同增益，甚至损害性能，证明是轨迹的结构（系统性和局部增量性）而非长度促使学习。
- **下一个令牌置信度与可学习性相关**：模型对 DFS 轨迹的下一个令牌预测置信度更高，训练损失曲线出现“尤里卡”式突降，表明连贯的局部预测路径使优化更容易。
- **非零温度的正则化效应**：对于随机冗余轨迹（RR）或混合顺序（η=0），适当提高采样温度反而能生成长度符合预期的轨迹并提升准确率。

## 7. 优点
- **受控实验环境**：通过定制分词器和合成图任务，将推理策略与性能进行解耦研究，排除了自然语言歧义和数据噪声等干扰。
- **明确的推理效率参数化**：通过温度参数 η 精准控制探索顺序，使低效轨迹与高效轨迹的比较变得清晰。
- **多维评估**：不仅关注答案准确率，还深入分析了 CoT 步骤质量、下一个令牌置信度、训练动态等，提供了对为何低效轨迹更有效的机理解释。
- **发现具有反直觉启发性**：揭示了下一个令牌预测模型的归纳偏好——“教最优”不如“教结构”，为 LLM 推理训练策略设计提供了重要参考。

## 8. 不足与局限
- **任务与语言的局限性**：仅在一个合成算法任务和自定义符号语言上验证，结论能否迁移到自然语言或多模态推理场景尚不清晰。
- **算法领域单一**：仅限于最短路径问题；排序、SAT、定理证明等不同算法可能呈现不同的最优-低效权衡。
- **模型规模有限**：主要使用 3 层小型 transformer，更大规模或不同架构（如非自回归模型）的归纳偏好可能不同。
- **训练数据覆盖**：虽然图实例是无限的，但推理轨迹均由一个预定义的探索算法生成，模型只能模仿该行为的模式，可能未涵盖真实推理的多样性。
- **未探索模型压缩推理的能力**：未来可研究是否可以通过课程学习或强化学习引导模型内部化更紧凑的推理策略。

（完）
