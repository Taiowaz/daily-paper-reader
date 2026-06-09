---
title: "$\\texttt{G1}$: Teaching LLMs to Reason on Graphs with Reinforcement Learning"
title_zh: G1：通过强化学习教授大语言模型图推理能力
authors: "Xiaojun Guo, Ang Li, Yifei Wang, Stefanie Jegelka, Yisen Wang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=Lq4nneD2xX"
tags: ["query:graph-llm"]
score: 10.0
evidence: 利用强化学习提升大语言模型在图任务上的推理能力
tldr: 大语言模型在图推理任务上表现有限，现有方法面临大规模图数据稀缺的挑战。G1创新地采用强化学习，在合成的大规模图论数据集Erdos上训练LLM，该数据集包含50种多样化的图任务。通过精心设计的奖励机制，模型学会了图结构推理，实验表明其在多个图推理基准上显著超越现有方法，为图增强LLM训练开辟了新途径。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-lq4nned2xx/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 579, \"height\": 339, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lq4nned2xx/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1428, \"height\": 769, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lq4nned2xx/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 364, \"height\": 276, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lq4nned2xx/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 368, \"height\": 272, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lq4nned2xx/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 580, \"height\": 352, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1440, \"height\": 585, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1155, \"height\": 856, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1026, \"height\": 176, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1024, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 716, \"height\": 405, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 729, \"height\": 428, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 699, \"height\": 410, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 715, \"height\": 431, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1154, \"height\": 260, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1380, \"height\": 149, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1454, \"height\": 206, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1025, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1171, \"height\": 135, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1022, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1025, \"height\": 173, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 666, \"height\": 191, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1168, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1166, \"height\": 284, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1458, \"height\": 512, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1458, \"height\": 399, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1459, \"height\": 532, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1458, \"height\": 546, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1258, \"height\": 2370, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1157, \"height\": 306, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1304, \"height\": 432, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 1446, \"height\": 2031, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 1445, \"height\": 2312, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 1444, \"height\": 2155, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 1445, \"height\": 2019, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-030.webp\", \"caption\": \"\", \"page\": 0, \"index\": 30, \"width\": 1444, \"height\": 1945, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-031.webp\", \"caption\": \"\", \"page\": 0, \"index\": 31, \"width\": 1445, \"height\": 1942, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-032.webp\", \"caption\": \"\", \"page\": 0, \"index\": 32, \"width\": 1446, \"height\": 2310, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-033.webp\", \"caption\": \"\", \"page\": 0, \"index\": 33, \"width\": 1445, \"height\": 2103, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-034.webp\", \"caption\": \"\", \"page\": 0, \"index\": 34, \"width\": 1447, \"height\": 1816, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lq4nned2xx/table-035.webp\", \"caption\": \"\", \"page\": 0, \"index\": 35, \"width\": 1448, \"height\": 1495, \"label\": \"Table\"}]"
motivation: 现有LLM在图推理任务上能力不足，且缺乏大规模标注图数据。
method: 构建大规模合成图任务集Erdos，采用强化学习训练LLM图推理。
result: 训练的LLM在多种图推理任务上达到领先性能，显著超越基线。
conclusion: 强化学习能有效提升LLM的图推理能力，是图增强训练的新范式。
---

## Abstract
Although Large Language Models (LLMs) have demonstrated remarkable progress, their proficiency in graph-related tasks remains notably limited, hindering the development of truly general-purpose models. Previous attempts, including pretraining graph foundation models or employing supervised fine-tuning, often face challenges such as the scarcity of large-scale, universally represented graph data. We introduce $\texttt{G1}$, a simple yet effective approach demonstrating that Reinforcement Learning (RL) on synthetic graph-theoretic tasks can significantly scale LLMs' graph reasoning abilities. To enable RL training, we curate \erdos, the largest graph reasoning dataset to date comprising 50 diverse graph-theoretic tasks of varying difficulty levels, 100k training data and 5k test data, all drived from real-world graphs. With RL on \erdos, $\texttt{G1}$ obtains substantial improvements in graph reasoning, where our finetuned 3B model even outperforms Qwen2.5-72B-Instruct (24x size). RL-trained models also show strong zero-shot generalization to unseen tasks, domains, and graph encoding schemes, including other graph-theoretic benchmarks as well as real-world node classification and link prediction tasks, without compromising general reasoning abilities. Our findings offer an efficient, scalable path for building strong graph reasoners by finetuning LLMs with RL on graph-theoretic tasks, which combines the strengths of pretrained LLM capabilities with abundant, automatically generated synthetic data, suggesting that LLMs possess graph understanding abilities that RL can elicit successfully. Our implementation is open-sourced at https://github.com/PKU-ML/G1, with models and datasets hosted on Hugging Face collections https://huggingface.co/collections/PKU-ML/g1-683d659e992794fc99618cf2 for broader accessibility.

---

## 论文详细总结（自动生成）

# G1: Teaching LLMs to Reason on Graphs with Reinforcement Learning 论文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：尽管大型语言模型（LLM）在许多自然语言任务上取得了显著进展，它们在**图结构数据推理**上的能力仍然非常有限，这阻碍了通用智能模型的发展。
- **现有方法的局限**：
  - 预训练图基础模型或使用监督微调（SFT）受限于**大规模、通用图数据的稀缺**。
  - 即使最先进的推理模型（如OpenAI o1）在图连通性测试上也仅有约58.49%的准确率。
- **整体含义**：本文提出通过**强化学习（RL）在合成图论任务上训练LLM**，可以显著释放并提升其内在的图推理能力，为构建强图推理器提供一条数据高效、可扩展的路径。

## 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：不再依赖人类标注数据，而是利用**可验证的合成图论任务**，通过RL的试错机制，激发LLM预训练中已潜藏的图理解能力。
- **数据集构建 – Erdős**：
  - 收集了**50种多样化图论任务**（从简单的节点计数到NP难问题如最大独立集），分为Easy、Medium、Hard、Challenging四个难度级别。
  - 从真实世界图（Network Repository）中通过随机游走采样子图（5~35节点），生成**10万训练样本 + 5千测试样本**。
  - 每个任务都配有可自动化验证的黄金答案或验证程序。
- **奖励设计**：
  - **严格值匹配**：对于唯一答案（如节点数），正确奖励+1，否则0。
  - **Jaccard指数**：对于无序集合答案（如公共邻居），奖励为预测集与真实集的Jaccard相似度，允许部分奖励。
  - **算法验证**：对于有多解问题（如最短路径），实现特定验证器检查解的正确性。
- **RL算法 – GRPO**：
  - 采用**Group Relative Policy Optimization (GRPO)** 算法。
  - 对于每个问题，采样一组响应，基于组内奖励的均值和标准差计算相对优势 \(A_i\)。
  - 策略模型 \(\pi_\theta\) 通过最大化带裁剪和KL散度约束的目标函数更新：
    \[
    J_{\mathrm{GRPO}}(\theta) = \mathbb{E}_{q,\{o_i\}} \left[ \frac{1}{G}\sum_{i=1}^G \min\!\left( \frac{\pi_\theta(o_i|q)}{\pi_{\theta_{\text{old}}}(o_i|q)} A_i,\; \text{clip}\!\left(\frac{\pi_\theta(o_i|q)}{\pi_{\theta_{\text{old}}}(o_i|q)}, 1-\epsilon, 1+\epsilon\right) A_i \right) - \beta D_{\text{KL}}(\pi_\theta \|\pi_{\text{ref}}) \right]
    \]
  - KL惩罚防止模型偏离基模型过远。
- **可选SFT预热**：
  - **Direct‑SFT**：直接在问答对上微调（无推理步骤）。
  - **CoT‑SFT**：使用更强大的模型（Qwen2.5‑32B‑Instruct）通过拒绝采样生成正确的思维链（CoT）作为训练数据，然后在RL前进行监督微调，以解决困难任务初始奖励信号稀疏的问题。
- **训练流程**：RL阶段（300步）+ 可选的SFT预热，均在Erdős数据集上进行。

## 3. 实验设计：数据集/场景、benchmark、对比方法
- **主要评估基准**：**Erdős测试集**（50个任务，5000样本），按难度分四类。
- **对比模型**：
  - 闭源模型：GPT‑4o‑mini、OpenAI o3‑mini（含工具使用）。
  - 开源指令模型：Qwen2.5‑Instruct（3B, 7B, 72B）、Qwen2.5‑Math‑Instruct、Llama‑3 系列（3B, 8B, 70B）。
  - 专门图训练模型：GraphWiz‑RFT、GraphWiz‑DPO。
  - 强推理基线：DeepSeek‑R1‑Distill‑Qwen‑7B。
  - 本方法的变体：Direct‑SFT‑3B/7B、CoT‑SFT‑3B/7B、G1‑3B/7B、G1‑Zero‑3B/‑7B/‑32B、G1‑Hard‑3B。
- **泛化实验**：
  - **其他图推理基准**：GraphWiz（任务分布和编码不同）、GraphArena（人名编码节点）。
  - **真实图任务**：Cora和PubMed上的节点分类与链接预测（结合文本属性）。
  - **通用推理能力**：GSM8K（数学）、MATH、MMLU‑Pro（多学科）。
- **鲁棒性验证**：32次不同随机种子运行、3个语义等价提示变体测试。

## 4. 资源与算力
- **主要训练配置**：
  - 3B和7B模型的RL训练在**8×A800 GPU集群**上进行，共训练**300步**，batch size为512，上下文长度4096。
  - CoT‑SFT数据生成使用Qwen2.5‑32B‑Instruct，对每个问题采样8次。
- **32B模型扩展**：G1‑Zero‑32B的训练耗时**40小时**，使用**32×A100 GPU**。
- **推理**：采用vLLM引擎进行高效批量推理。
- 论文未报道更详细的训练总时长（如wall-clock time），但提供了显存的利用方式（GPU数、batch size、梯度累积步数）。

## 5. 实验数量与充分性
- **实验组数**：覆盖了多模型家族、多参数规模、多种训练策略的对比，形成约**二十余个模型条目**在多个基准上的完整结果。
- **消融研究**：
  - SFT预热的影响（G1 vs. G1‑Zero）。
  - 数据混合策略（仅训练困难任务的G1‑Hard‑3B）。
  - 奖励加权（G1‑Soft‑3B）。
  - 推理模式的案例分析（最短路径任务中的 BFS、Dijkstra、直觉策略分布）。
- **可重复性验证**：多随机种子实验显示标准差<1%；不同提示词变体测试显示标准差<1.5%，证明了结果的稳定性。
- **公平性**：所有开放模型均使用统一解码参数和提示格式，答案提取方法一致（\boxed{}）。
- 实验设计系统、覆盖维度广，消融对比充分，体现了较强的客观性和可信度。

## 6. 论文的主要结论与发现
- **核心结论**：RL 能够有效且可扩展地提升 LLM 在图推理任务上的性能。
- **具体发现**：
  - **Erdős基准**：G1‑7B 平均准确率达66.16%，超越 GPT‑4o‑mini（+18.56%），与 o3‑mini（64.90%）持平；G1‑3B（59.76%）超越 Qwen2.5‑72B‑Instruct（47.16%），显示极高参数效率。
  - **泛化能力**：
    - 在 GraphWiz 和 GraphArena 上零样本性能大幅领先特定训练的图模型（如 GraphWiz‑DPO）。
    - 在真实图任务（Cora/PubMed 节点分类和链接预测）上显著超过基模型和对比模型。
    - 通用推理（GSM8K, MATH, MMLU‑Pro）不仅未下降，G1‑7B 甚至略有提升，且改善了数值计算准确性和信息利用率。
  - **训练策略**：CoT‑SFT 预热有助于困难任务的学习；直接 RL（G1‑Zero）也能取得很强的性能，但整体不如 SFT+RL。
  - **推理行为变化**：RL 训练使模型放弃低效的 Dijkstra 算法，转而采用 BFS 和直觉搜索结合的策略，表明模型学会了适应自身能力的推理方式。
  - **数据效率**：仅需 300 步 RL 训练即可达到优异结果，合成数据驱动的方式绕开了人工标注瓶颈。

## 7. 优点：方法或实验设计上的亮点
- **创新性**：**首次**将 RL（RLVR 范式）应用于 LLM 图推理，证明了该路径的有效性。
- **数据集贡献**：构建了**迄今最大、最全面的图论推理数据集 Erdős**，基于真实图，涵盖 50 个任务，为训练和评估提供了可靠平台。
- **可扩展性**：方法可轻松扩展到更大模型（32B 展示）和更大图（36–100 节点零样本泛化有效）。
- **泛化能力突出**：在未见任务、编码格式、真实图任务上均表现出强零样本迁移，且不牺牲通用推理能力。
- **稳健的分析**：多种子、多提示实验验证结果稳定；深入案例分析揭示了 RL 对推理策略的积极影响。
- **开源与可复现**：代码、模型和数据集均公开，并提供了详细的实验配置。

## 8. 不足与局限
- **样本效率**：面对 NP-hard 等极难任务，通常只会产生不正确样本，导致 RL 训练信号稀疏，文中仅在 Hard‑Only 或调整奖励权重后部分缓解，未根本解决。
- **图规模限制**：受限于 LLM 的上下文窗口（如 Qwen2.5‑7B 的 32k tokens），所处理的图规模仅到 100 节点左右，超大规模图（>1000 节点）尚无法直接应用。
- **领域泛化测试有限**：虽然展示了在引文网络上的节点分类和链接预测效果，但未测试分子性质预测、交通网络等高度领域特定任务。
- **训练成本**：RL 训练需要生成多个响应并计算奖励，相比纯 SFT 计算开销较大；文中未提供不同规模模型的具体训练时长和显存消耗对比。
- **奖励加权策略**：均匀加权或固定难度系数的奖励加权仍是粗糙的；动态难度调度可能更优但未被探索。
- **可解释性**：虽然给出了策略变化的案例分析，但对 RL 如何具体重塑内部推理过程的机理性解释尚不深入。

（完）
