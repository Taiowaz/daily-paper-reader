---
title: "Graph-KV: Breaking Sequence via Injecting Structural Biases into Large Language Models"
title_zh: Graph-KV：通过注入结构偏置突破大型语言模型的序列限制
authors: "Haoyu Peter Wang, Peihao Wang, Mufei Li, Shikun Liu, Siqi Miao, Zhangyang Wang, Pan Li"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=J4w4RtwLyB"
tags: ["query:graph-llm"]
score: 9.0
evidence: 向LLM注入结构偏置以通过打破序列限制处理图结构化数据
tldr: 针对大语言模型因自回归序列化而无法利用结构归纳偏置的局限，Graph-KV 将文本段的 KV 缓存作为压缩表示，并通过结构偏置控制段间注意力，使目标段仅关注图中指定源段的缓存。该方法突破了序列限制，在检索增强生成和图结构推理任务中展现了潜力，为 LLM 注入图结构认知开辟了新途径。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-j4w4rtwlyb/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1369, \"height\": 582, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-j4w4rtwlyb/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 622, \"height\": 303, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-j4w4rtwlyb/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1356, \"height\": 545, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-j4w4rtwlyb/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 524, \"height\": 332, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-j4w4rtwlyb/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 471, \"height\": 302, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-j4w4rtwlyb/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1371, \"height\": 407, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-j4w4rtwlyb/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1433, \"height\": 611, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-j4w4rtwlyb/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 673, \"height\": 257, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-j4w4rtwlyb/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 688, \"height\": 209, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-j4w4rtwlyb/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1450, \"height\": 356, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-j4w4rtwlyb/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1454, \"height\": 489, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-j4w4rtwlyb/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 669, \"height\": 379, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-j4w4rtwlyb/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1455, \"height\": 235, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-j4w4rtwlyb/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1456, \"height\": 243, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-j4w4rtwlyb/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1454, \"height\": 250, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-j4w4rtwlyb/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1448, \"height\": 251, \"label\": \"Table\"}]"
motivation: LLM 的自回归序列化特性导致其无法利用图结构中的归纳偏置，影响检索增强生成与推理性能。
method: Graph-KV 利用文本段 KV 缓存作为紧凑表示，并基于图结构偏置控制段间注意力，使目标段仅关注指定源段，打破线性序列约束。
result: 在需要图结构交互的任务中，该方法能有效注入结构信息，克服序列化带来的限制。
conclusion: Graph-KV 为 LLM 处理图结构化数据提供了一种新范式，通过结构偏置提升模型对图依赖的建模能力。
---

## Abstract
Modern large language models (LLMs) are inherently auto-regressive, requiring input to be serialized into flat sequences regardless of their structural dependencies. This serialization hinders the model’s ability to leverage structural inductive biases, especially in tasks such as retrieval-augmented generation (RAG) and reasoning on data with native graph structures, where inter-segment dependencies are crucial. 
We introduce Graph-KV with the potential to overcome this limitation. Graph-KV leverages the KV-cache of text segments as condensed representations and governs their interaction through structural inductive biases. In this framework, ''target'' segments selectively attend only to the KV-caches of their designated ''source'' segments, rather than all preceding segments in a serialized sequence. This approach induces a graph-structured block mask, sparsifying attention and enabling a message-passing-like step within the LLM. Furthermore, strategically allocated positional encodings for source and target segments reduce positional bias and context window consumption. 
We evaluate Graph-KV across three scenarios: (1) seven RAG benchmarks spanning direct inference, multi-hop reasoning, and long-document understanding; (2) Arxiv-QA, a novel academic paper QA task with full-text scientific papers structured as citation ego-graphs; and (3) paper topic classification within a citation network.
By effectively reducing positional bias and harnessing structural inductive biases, Graph-KV substantially outperforms baselines, including standard costly sequential encoding, across various settings.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- 现代LLM（如GPT、LLaMA等）本质上是自回归模型，必须将输入数据序列化为一维的线性序列，即使数据本身具有复杂的结构依赖关系（如RAG中无序的检索片段、论文间的引用网络等）。
- 这种强制序列化带来了三个核心问题：
  - **位置偏差（Positional Bias）**：不同排列顺序会导致模型输出不一致。
  - **注意力二次复杂度**：所有片段之间进行全注意力计算，计算开销随片段数呈二次增长。
  - **上下文窗口快速消耗**：位置索引随序列长度迅速增长，易超出模型窗口限制。
- 因此，核心研究问题是：**如何将数据的结构归纳偏置直接注入到LLM的推理过程中，使其能突破线性序列的桎梏，高效且鲁棒地处理结构化依赖**。
- Graph‑KV 的整体含义是：通过将文本片段的键值（KV）缓存视为压缩表示，并利用图结构定义片段之间的注意力规则，在LLM内部实现一种“类消息传递”的结构化信息融合，从而有效缓解上述问题。

## 2. 论文提出的方法论

### 核心思想
- 不再将文本片段按某一顺序串行输入LLM，而是先独立编码得到各片段的初始化KV缓存 `(k^{(0)}_{u_i}, v^{(0)}_{u_i})`。
- 根据预先定义的结构偏置（如RAG中检索相关性构建的二分图、论文间的引用关系等），形成**有向图 `G=(V,E)`**，每条边`(u→v)`表示片段`u`是片段`v`的“源”，片段`v`需要通过注意力从源片段中提取信息。

### 关键技术细节
1. **结构感知注意力机制**  
   - 对图中的每条有向边进行稀疏注意力更新：  
     - 目标片段 `u_j` 只关注其源片段集合 `N(j)` 的KV缓存，注意力公式为 `softmax(Q_j K_{N(j)}^T / √d_h) V_{N(j)}`。  
     - 这等价于在图结构上做一次“消息传递”，使目标片段的表示融合了其结构依赖信息。  
   - 更新后的KV缓存可与原始缓存一起被后续解码过程使用。

2. **共享位置编码（PE）策略**  
   - 所有源片段被分配到相同的PE范围 `[0, L)`（假设片段长度≤ L）。  
   - 所有目标片段紧接着共享后续的PE范围 `[L, 2L)`。  
   - 查询令牌及生成的答案从 `2L` 之后继续编号。  
   - 这种设计大幅降低了总位置索引的使用量（约 `T·L`，T为迭代轮数，通常很小），有效缓解上下文窗口膨胀问题，同时削弱位置偏差。

3. **复杂度分析**  
   - 初始编码复杂度 `O(|V|L^2)`，更新目标片段的复杂度 `O(|E|L^2)`，生成阶段注意力复杂度 `O(|V|L)`，整体效率远优于全序列的二次复杂度。

### 算法流程（文字概括）
- 步骤1：独立预填充所有片段的KV缓存。
- 步骤2：按图边定义，源片段KV保持不变，目标片段仅对其源片段集合执行一次稀疏注意力，更新其KV缓存。
- 步骤3：将查询令牌与所有片段（源+目标）的KV缓存进行全注意力，生成答案。

## 3. 实验设计

### 评估场景与数据集
1. **任务1 – RAG基准（无原生图结构）**  
   - 数据集：NarrativeQA、TriviaQA、HotpotQA、2Wiki、Multihop‑RAG、MorehopQA、LongBenchV2。  
   - 涵盖直接推理、多跳推理、长文档理解。  
   - 结构偏置通过检索相关性构建的二分图引入（Top‑m 源片段，其余目标片段，或全连接变体）。

2. **任务2 – Arxiv‑QA（原生引用图）**  
   - 自己构建的学术论文问答数据集：60篇主论文及其引用论文全文，需要跨引用关系的技术细节推理。  
   - 加入 0/1/2 个干扰项（整个论文引用子图）测试位置鲁棒性和超长上下文能力。

3. **任务3 – 论文主题分类（原生引用网络）**  
   - 使用 Cora 和 Pubmed 图数据，用LLM分类中心论文，基于标题和摘要，可引用数百篇参考文献。

4. **任务4 – 可扩展性压力测试（合成星形图）**  
   - 测试GPU内存占用和首令牌延迟（TTFT），对比顺序编码。

### 对比方法
- **顺序编码**：标准LLaMA‑3.1‑8B‑SFT / RAG / Block‑FT 的串行输入。
- **并行编码基线**：PCW、APE、Block‑RAG（其中Block‑RAG与Graph‑KV共享相同的微调骨干）。
- **Graph‑KV 变体**：Top‑1、Top‑3、Full（全连接图）。
- 注：Arxiv‑QA 和论文分类中，还对比了顺序编码中答案片段放置在不同位置时的性能差异，以体现位置偏差。

## 4. 资源与算力（论文提及情况）

- **GPU型号与数量**  
  - Arxiv‑QA任务：并行编码基线及Graph‑KV使用 **4×NVIDIA A100 (80G)**，顺序编码基线因内存需求更高使用 **8×A100**。  
  - 其他所有任务：使用 **NVIDIA RTX 6000 Ada** 显卡。
- **CPU**：压力测试中使用 AMD EPYC 7763 64‑core 处理器。
- **训练时长**：论文中未明确给出微调所用时间，但强调Graph‑KV本身**未直接进行微调**，主模型为已有的Llama‑3.1‑8B‑Block‑FT。该预训练模型是在tulu‑3和RAG数据上后训练得到，但未提供具体训练时间。

## 5. 实验数量与充分性

- 实验组数量庞大，大致涵盖：
  - 7个RAG数据集 × 多个变体（Graph‑KV Top‑1/Top‑3/Full）× 5种以上基线方法。
  - Arxiv‑QA 60个问题 × 0/1/2干扰项 × 位置变化 × 多种方法。
  - 2个节点分类图 × 多种方法（含随机种子多次实验）。
  - 压力测试：内存和TTFT随节点数/单词数变化曲线。
  - 配套消融：附录中包含不同骨干（通用LLM）、多跳图构造（2‑hop、3‑hop）等补充实验。
- **充分性评价**：实验覆盖了无图结构、原生图结构、学术长文、分类任务等场景，对比全面，消融丰富，并展示了效率指标，整体较为**充分、客观、公平**。  
- 潜在局限性：未将Graph‑KV在不同LLaMA规模（如13B/70B）及其他模型家族上测试。

## 6. 论文的主要结论与发现

1. Graph‑KV 通过引入图结构掩码和共享位置编码，成功将结构归纳偏置注入LLM注意力计算中，显著提升了模型利用数据间依赖关系的能力。
2. 在需要多跳推理的RAG任务中（如Multihop‑RAG、MorehopQA），Graph‑KV‑Top‑3 甚至**超越顺序编码**达 2%‑10%，同时保持稀疏计算。
3. 在 Arxiv‑QA 超长上下文、带干扰项的设定下，顺序编码表现出严重的位置偏差（答案放序列开头时性能骤降），而Graph‑KV几乎无位置偏差，且效果持续最优。
4. 效率上，Graph‑KV可编码的邻居数量是顺序编码的3倍以上，TTFT显著降低（得益于预填充），并节省上下文窗口。
5. 在论文主题分类任务中，Graph‑KV 首次不依赖适配器，直接通过修改注意力机制实现图结构数据理解，且性能优于并行和顺序基线。

## 7. 优点（方法或实验设计的亮点）

- **方法创新**：首次直接在LLM的注意力机制层面注入结构偏置，而非依赖序列化或适配器，开创了一种“结构提示”的新范式。
- **简洁而高效**：通过共享PE和稀疏图注意力，既缓解了位置偏差，又极大降低了上下文占用和计算开销，适应超长文本场景。
- **多任务验证**：设计并验证了三个截然不同的真实应用场景（RAG、学术全文学位推理、图节点分类），证明方法的通用性。
- **新任务贡献**：贡献了具有挑战性的 Arxiv‑QA 数据集，要求理解全文和跨论文引用关系，可用于后续研究。
- **深入的位置偏差分析**：通过干扰项和位置摆放实验，清晰展示了顺序编码的脆弱性及Graph‑KV的鲁棒性。

## 8. 不足与局限（包括实验覆盖、偏差风险、应用限制等）

- **依赖性一跳更新**：当前仅实现单轮消息传递（一跳更新），未展示多轮迭代能否进一步提升，作者也承认复杂任务可能需多轮，但尚未探索。
- **微调依赖**：Graph‑KV 性能高度依赖“独立块注意力”预训练（Block‑FT），若直接在通用预训练模型上应用，性能下降明显；且未对Graph‑KV自身的结构注意力进行专门微调，限制了潜力。
- **模型与规模泛化**：全部实验基于LLaMA‑3.1‑8B，未在更大模型或其他架构（如Qwen、Mistral等）上验证，结论的普遍性待考。
- **图结构定义依赖**：对于无天然图结构的场景，需人工定义二分图或全连接图，且选择“源‑目标”的方式会引入额外超参数（如Top‑m），最优构造策略在不同任务上可能不同。
- **实验任务局限**：虽有多任务评估，但缺少与基于GNN+LLM混合方法（如GraphGPT、Gofa等）的直接对比，削弱了该类任务上的说服力。
- **理论分析欠缺**：论文未对结构偏置注入后的信息传播过程、收敛性提供理论支撑，主要依赖经验证据。

（完）
