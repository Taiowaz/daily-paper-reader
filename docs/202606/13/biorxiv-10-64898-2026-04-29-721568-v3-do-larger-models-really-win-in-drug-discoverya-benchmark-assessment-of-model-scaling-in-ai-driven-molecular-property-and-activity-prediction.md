---
title: Do Larger Models Really Win in Drug Discovery?A Benchmark Assessment of Model Scaling in AI-Driven Molecular Property and Activity Prediction
title_zh: 在药物发现中，更大的模型真的胜出吗？人工智能驱动的分子性质与活性预测中模型规模的基准评估
authors: "Guo, J., Ding, S."
date: 2026-06-08
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.29.721568v3.full.pdf"
tags: ["query:graph-llm"]
score: 8.0
evidence: 在分子性质预测中基准测试LLM与图神经网络，评估LLM在图结构分子数据上的表现。
tldr: "随着分子基础模型和大语言模型（LLMs）的快速发展，药物发现中兴起“规模中心”观点，认为更大预训练模型将优于紧凑的化学信息学模型。我们在26个端点（ADME、毒性、生物活性）上，采用从易到难的随机、Murcko骨架和结构分离三种数据划分，进行156项模型比较。结果：经典机器学习在47.4%比较中取得最佳，预训练分子序列模型占28.8%，图神经网络占21.8%，LLM仅1.9%；在更难划分下，GNN和序列模型在最优读出设置下具有竞争力，但固定窗口读出时优势减弱。结论：预测性能取决于模型、任务和验证场景的契合度，而非单纯规模；紧凑专用模型仍高度有效，大模型在低数据推理中有增值。"
source: biorxiv
selection_source: fresh_fetch
motivation: 随着大规模分子模型和LLM兴起，药物发现领域盛行“规模越大越好”的观点，亟需通过多端点、多划分方案的系统基准检验其真实优势。
method: 构建覆盖26个ADME、毒性、生物活性端点，采用随机、Murcko骨架和结构分离三种划分协议的基准，比较经典ML、GNN、序列模型和LLM共156项表现。
result: "经典ML胜率最高（47.4%），GNN与序列模型仅在难划分下略有竞争力，LLM仅占1.9%，配对bootstrap显示多数细微差异不显著。"
conclusion: 模型性能不取决于规模，而取决于模型、任务与验证场景的匹配；紧凑专用模型在预测中依旧高效，大模型在低数据推理中有增值。
---

## 摘要
分子基础模型和大语言模型的快速发展，催生了以规模为中心的人工智能药物发现观，即预期更大的预训练模型将取代基于传统机器学习（传统ML）和图神经网络（GNN）的紧凑化学信息学模型，这些模型曾为单个任务训练。我们在26个终点上检验了这一假设，这些终点分为ADME、毒性和生物活性三类，覆盖165,541个终点级别的化合物标签记录。基准包含78个终点与划分条目，对应26个终点，采用三种划分方案评估：随机划分、Murcko骨架划分和结构分离的五折交叉验证。从易到难，这些划分分别近似于封闭库的回溯评估、从苗头化合物到先导化合物的骨架扩展，以及新化学型的库扩展。每个条目贡献两项任务和指标比较，总计156项比较。在这些比较中，传统ML提供了最大比例的最佳表现条目（47.4%），其次是预训练分子序列模型（28.8%）、GNN（21.8%）和基于LLM的SAR基线（1.9%）。传统ML在随机划分插值中占主导地位，并总体保持最大赢家类别。在主要的保留最优读出下，GNN和序列模型在选定的较难划分方案中具有竞争力，但在固定的最终窗口读出下，它们的严格赢家比例下降，表明部分增益依赖于训练设置和模型选择。配对自助法分析表明，个别模型之间微小的数值差异不应被解读为决定性的胜利。训练折中的SAR知识提升了许多GPT5.5-SAR和Opus4.7-SAR指标，但并未使基于规则的推理成为监督预测器的普遍替代品。紧凑的专用模型在分子性质与活性预测中仍然非常有效。更大模型在低数据设置下的SAR解释和推理中增加价值，但预测性能取决于模型、任务和验证场景之间的适配，而非仅仅规模。

## Abstract
The rapid growth of molecular foundation models and large language models (LLMs) has encouraged a scale centred view of AI in drug discovery, in which larger pretrained models are expected to supersede compact cheminformatics models based on classical machine learning (classical ML) and graph neural networks (GNNs) trained for individual tasks. We test this assumption across 26 endpoints grouped into ADME, toxicity and bioactivity classes, covering 165,541 endpoint level compound label records. The benchmark contains 78 endpoint and split entries, corresponding to 26 endpoints evaluated under three split protocols: random, Murcko scaffold and structure separated 5-fold cross validation (CV). Ordered from easiest to hardest, these splits approximate retrospective evaluation on a closed library, scaffold expansion in hit to lead, and library expansion on novel chemotypes. Each entry contributes two task and metric comparisons, giving 156 comparisons in total. Across these comparisons, classical ML provides the largest share of best performing entries (47.4%), followed by pretrained molecular sequence models (28.8%), GNNs (21.8%) and LLM based SAR baselines (1.9%). Classical ML dominates random split interpolation and remains the largest winner family overall. GNN and sequence models are competitive in selected harder split protocols under the primary optimal held-out readout, but their strict winner shares decrease under a fixed final-window readout, indicating that some of these gains depend on training settings and model selection. Paired bootstrap analyses indicate that small numerical differences between individual models should not be read as decisive victories. SAR knowledge from training folds improves many GPT5.5-SAR and Opus4.7-SAR metrics but does not make rule based reasoning a universal substitute for supervised predictors. Compact specialized models remain highly effective for molecular property and activity prediction. Larger models add value for SAR interpretation and reasoning in low data settings, but predictive performance depends on the fit among model, task and validation scenario, not on scale alone.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义

- **研究动机**：近年来分子基础模型与大语言模型在药物发现中迅速崛起，业界出现“规模中心论”观点——即认为越大的预训练模型（如 LLM、大规模分子序列模型）会全面超越面向单一任务训练的紧凑型化学信息学模型（传统机器学习与图神经网络）。
- **核心问题**：在药物分子性质预测与活性预测的实际任务中，模型规模是否真的决定性能优势？大模型是否必然打败小模型？
- **整体含义**：论文通过多端点、多划分方案的系统基准测试，挑战规模至上假设，力图厘清哪些条件下紧凑专用模型依然具备竞争力，大模型又在哪些场景有增值空间。

### 2. 论文提出的方法论

- **核心思想**：构建统一、可比的评估框架，控制模型选择、训练设置（读出方式）和划分策略的影响，从而隔离“规模效应”的真实贡献。
- **关键技术细节**：
  - **端点与划分组合**：26 个 ADME、毒性及生物活性端点 × 三种划分方案（5 折交叉验证）= 78 个端点–划分条目。
    - `随机划分`：近似封闭库回溯评估（最易）。
    - `Murcko 骨架划分`：近似苗头化合物到先导化合物的骨架扩展（中等难度）。
    - `结构分离划分`：基于新颖化学型的库扩展（最难）。
  - **模型类型**：四类主干方法对比。
    - 传统 ML（经典机器学习/化学信息学模型）。
    - 预训练分子序列模型。
    - GNN 模型（图神经网络）。
    - 基于 LLM 的 SAR 基线（如 GPT5.5‑SAR、Opus4.7‑SAR，并可注入训练折 SAR 知识）。
  - **读出设置对比**：
    - 主要读出：`最优保留读出`（保留最优训练设置下的结果）。
    - 对照读出：`固定最终窗口读出`，用以暴露训练依赖的增益。
  - **统计分析**：配对自助法（paired bootstrap）检验个别模型间微小数值差异的显著性，避免激进结论。
- **算法流程（文字描述）**：对每个端点–划分条目，在相同数据划分下训练/预测各模型家族的代表方法，记录两种任务与指标（共 2 项指标），累计 156 项直接比较；比较“严格最佳”和“无显著优势”的频率，并按划分难度分层分析。

### 3. 实验设计

- **数据集与场景**：
  - 26 个端点，覆盖 ADME、毒性、生物活性，含 165,541 条化合物级别记录。
  - 三种划分难度梯度，刻画不同真实应用场景：从简单随机插值 → 骨架扩展 → 新化学型泛化。
- **Benchmark 构成**：
  - 78 个端点–划分条目，每条目对应 2 个任务/指标比较 → 共计 156 项直接比较。
- **对比方法**：
  - 经典 ML（化学信息学特征+传统机器学习）。
  - 预训练分子序列模型。
  - GNN 系列。
  - LLM‑based SAR 基线（如 GPT5.5‑SAR、Opus4.7‑SAR）。
  - 额外验证注入训练折 SAR 知识对 LLM 基线的影响。

### 4. 资源与算力

- 文中**未明确说明**使用了何种 GPU 型号、数量、训练时长等具体算力消耗。摘要及可获取内容未提及算力统计。若需确切数据，须查阅完整原文。

### 5. 实验数量与充分性

- **实验规模**：
  - 26 端点 × 3 划分 = 78 个条目，每条目 2 指标 = 156 项横向比较。
  - 进一步分层考察最优读出与固定窗口读出下的赢家分布差异。
- **充分性**：覆盖了多个药物发现关键性质类别和从易到难的泛化场景，实验设计系统。
- **客观性与公平性**：
  - 统一划分、多家族模型同期比较，配对自助法校正微小差异，减少了“侥幸胜出”风险。
  - 但对比的模型代表类型并非穷举，且部分 LLM 基线受训练折知识注入方式影响，可能仍存在方法选择偏好。

### 6. 论文的主要结论与发现

- **模型家族赢家分布**：
  - 经典 ML 贡献 **47.4%** 最佳条目，其次为预训练分子序列模型（28.8%）、GNN（21.8%），LLM‑based SAR 仅 **1.9%**。
  - 经典 ML 不仅在随机划分插值中占优，整体仍为第一赢家家族。
- **难度与模型表现关系**：
  - 在更难的划分下，GNN 和序列模型在最优保留读出下具有一定竞争力，但换成固定窗口读出时赢家比例下降，显示增益部分依赖训练设置与模型选择。
- **统计稳健性**：许多原始数值优势微小且不显著，不应被视为决定性胜利。
- **LLM 角色**：训练折 SAR 知识可改善某些 LLM‑SAR 指标，但基于规则的推理尚无法普遍替代监督预测器。
- **核心观点**：预测性能取决于**模型、任务与验证场景的适配度**，而非单纯由规模决定。紧凑专用模型在分子性质/活性预测中仍高度有效；大模型在低数据场景的 SAR 解释与推理中提供增值。

### 7. 优点

- **系统基准框架**：统一的多端点、多难度划分、多模型家族设计，提供药物发现 AI 的全面参考。
- **难点侧重**：明确区分插值、骨架扩展、新化学型泛化的难度层次，契合实际研发流程。
- **统计严谨性**：采用配对自助法，避免将微小数值差异过度解读。
- **训练依赖性分析**：通过最优与固定窗口读出对比，揭示模型性能对训练设置的选择依赖性，防止高估特定模型家族。
- **结论平衡**：既肯定紧凑专用模型的实用性，又识别大模型在低数据推理场景的价值，避免一边倒结论。

### 8. 不足与局限

- **方法覆盖有限**：仅选取各家族代表性方法，未全面涵盖所有新型分子模型或最新 LLM 变体。
- **数据容量与多样性**：26 端点、约 16 万条记录，虽具一定广度，但仍难以代表所有药物发现终点和化学空间。
- **LLM‑SAR 基线设置依赖**：LLM‑SAR 表现受训练折知识注入方式影响，可能低估或高估其真实潜力。
- **算力与效率未比较**：未评估模型规模增长带来的计算成本与延迟，而这在实际部署中至关重要。
- **潜在偏差**：实验设置（如固定窗口读出定义）可能偏利好某些模型类型，且部分结论可能受所选基准任务性质（主要为性质预测）限制。

（完）
