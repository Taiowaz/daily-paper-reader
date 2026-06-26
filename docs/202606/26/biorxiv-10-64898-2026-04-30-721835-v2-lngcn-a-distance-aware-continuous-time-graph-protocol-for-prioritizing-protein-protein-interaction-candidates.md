---
title: "LNGCN: a distance-aware continuous-time graph protocol for prioritizing protein-protein interaction candidates"
title_zh: LNGCN：一种用于优先化蛋白质-蛋白质相互作用候选物的距离感知连续时间图协议
authors: "Xiao, Y., Zheng, Y., Hua, Y., Peng, J., Liu, J., Qu, Y., Xu, J., Fu, R., Qian, Q., Zhao, M., Zhang, X., Zhao, J., Yao, Y., Kosar, M., Ke, Y., Chi, Y."
date: 2026-06-25
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.30.721835v2.full.pdf"
tags: ["query:dynamic-g"]
score: 8.0
evidence: 提出一种结合液体神经动态的连续时间图神经网络协议，用于建模动态图演化，适用于时序图学习。
tldr: 准确预测蛋白质-蛋白质相互作用（PPI）对映射细胞机制和指导实验验证至关重要，但现有图方法常因离散消息传递导致表示过平滑和置信度校准差。LNGCN提出距离感知的连续时间图协议，整合残基层次结构图与液体神经动力学，以残基径向距离作为显式驱动信号实现图演化，并通过层次校准输出可解释概率。在平衡、高度不平衡和跨物种基准上取得稳健性能，校准分数在FGF23–FGFR1c–Klotho复合体、SHP2信号通路和Tdk1寡聚态依赖性结合中支持了生物学一致的优先化。在TPR案例研究中，LNGCN恢复已知互作并优先化ELAVL1-TPR和RALY-TPR，经实验验证其物理相互作用，证明该协议可作为实用的PPI候选优先化工具。
source: biorxiv
selection_source: fresh_fetch
motivation: 当前PPI预测的图方法受离散传递、过平滑和置信度校准差的限制，难以有效支撑实验优先化。
method: LNGCN利用残基径向距离驱动连续时间图演化，融合结构图与液体神经动力学，并通过层次校准输出可解释的相互作用概率。
result: 在多种基准上实现了稳健预测，校准分数在FGF23复合体等案例中展现了生物学一致性，实验验证了ELAVL1-TPR和RALY-TPR的预测相互作用。
conclusion: LNGCN提供了一种距离感知的连续时间PPI优先化协议，其校准分数能可靠指导实验验证，具有实用价值。
---

## 摘要
准确的蛋白质-蛋白质相互作用（PPI）高通量预测对于绘制细胞机制图谱和优先化实验验证至关重要。当前的基于图的方法通常依赖于离散消息传递，存在表示过度平滑的问题，并且提供的置信度分数校准不佳。我们提出了LNGCN，一种距离感知的连续时间图协议，该协议将残基级结构图与液态神经动力学相结合，以建模空间异质性相互作用模式。残基径向距离被用作连续图演化的显式驱动信号，而分层校准则将原始模型输出转换为可解释的相互作用概率。在平衡、高度不平衡和跨物种基准测试中，LNGCN实现了稳健的预测性能。重要的是，校准后的分数在FGF23-FGFR1c--Klotho复合物、SHP2相关信号传导相互作用和Tdk1寡聚态依赖性结合中支持生物学上一致的优先化。在以TPR为中心的实验案例研究中，LNGCN恢复了已知的TPR相关伙伴，并优先化了ELAVL1-TPR和RALY-TPR，其物理相互作用随后通过实验验证得到确认。这些结果表明，LNGCN可以作为PPI候选物的实用优先化协议。

## Abstract
Accurate high-throughput prediction of protein-protein interactions (PPIs) is essential for mapping cellular mechanisms and prioritizing experimental validation. Current graph-based methods often rely on discrete message passing, suffer from representation over-smoothing, and provide poorly calibrated confidence scores. We present LNGCN, a distance-aware continuous-time graph protocol that integrates residue-level structural graphs with liquid neural dynamics to model spatially heterogeneous interaction patterns. Residue radial distance is used as an explicit driving signal for continuous graph evolution, while hierarchical calibration converts raw model outputs into interpretable interaction probabilities. Across balanced, highly imbalanced, and cross-species benchmarks, LNGCN achieved robust predictive performance. Importantly, the calibrated scores supported biologically coherent prioritization in the FGF23-FGFR1c--Klotho complex, SHP2-associated signaling interactions and Tdk1 oligomeric-state-dependent binding. In a TPR-centered experimental case study, LNGCN recovered known TPR-associated partners and prioritized ELAVL1-TPR and RALY-TPR, whose physical interactions were subsequently confirmed via experimental validation. These results indicate that LNGCN can serve as a practical prioritization protocol for PPI candidates.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义
- 蛋白质‑蛋白质相互作用（PPI）是细胞过程的核心，实验验证成本高、通量低，计算预测与候选排序成为关键。
- 现有基于图的方法（如 GCN）主要问题：
  - 依赖离散消息传递，难以建模残基连续的空间层级，导致表示过平滑、空间信息被抹平。
  - 直接将不校准的原始分数用于排序，置信度不可靠，不利于实验决策。
- 本文旨在提供一种距离感知的连续时间图协议，将结构信息转化为可解释的校准概率，用于高通量 PPI 筛选和实验优先化。

## 2. 方法论
- **整体流程（Siamese 架构）**
  两个输入蛋白通过共享的编码模块独立处理，再融合为图级表示进行交互预测。
- **关键阶段**
  1. 残基级图构建与特征提取  
     - 每个蛋白构建为接触图，节点为残基，边为空间接触。  
     - 节点特征：1803 维（ESM‑2 序列表示、ESM‑IF1 结构表示、DSSP 二级结构、溶剂可及性等）+ 1 维归一化径向距离 \( r_i \)（残基到蛋白中心的距离归一化）。
  2. CfC 预处理  
     - 使用闭式连续时间网络（CfC）作为门控投影，将高维特征压缩至 256 维，同时保留径向距离不变。  
     - 公式：输出由 Sigmoid 门控在动态和静态分支间插值。
  3. 距离感知图驱动 LNN 模块  
     - 将 CfC 输出送入液态时间常数网络（LNN），每个残基节点遵从 ODE：  
       \(\displaystyle \frac{d\mathbf{h}_i}{dt} = -\left(\frac{1}{\tau} + f_i\right) \odot \mathbf{h}_i + A \odot f_i\)  
     - 驱动项 \(f_i\) 结合 GCN 聚合的邻域结构信息与径向距离嵌入，实现空间异质性演化。  
     - 采用隐式欧拉离散化保证数值稳定；多轮迭代后通过多跳图卷积与残差融合，得到图级表示（平均池化）。
  4. 蛋白对对称融合与 LNN 稠密分类器  
     - 两蛋白质图表示通过求和、逐元素积、绝对差进行对称融合。  
     - 融合向量送入两层 LNN 稠密动态模块（离散化 ODE），最后线性投影输出二元 logits。
  5. 多方法概率校准  
     - 使用四种校准器：Platt、Beta、Isotonic、Boosting。  
     - 在每一交叉验证折内分别拟合，再取方法平均后，跨折袋平均得到最终校准概率 \(\hat p_i^{\text{ensemble}}\)，用于排序和阈值筛选。

## 3. 实验设计
- **数据集**
  - 主数据集：STRING 分数 >0.9 的正样本 + 随机非交互负样本，分训练、验证、测试集。
  - 高度不平衡数据集：Zhang 等 2025 的 1:10 人 PPI 数据集。
  - 跨物种泛化：酵母 PPI 数据（STRING）。
  - 校准集：3000 正（Zhang 集交集）+3000 负（包含 Negatome）。
- **对比方法**
  - 主基准：PIPR（Siamese 残差轮回网络）、SWING（滑动窗口语言模型）。
  - 不平衡场景：RF2‑PPI。
- **评估指标**
  - AUPRC、AUROC、Accuracy、Precision、Recall、F1、MCC、PR/ROC 曲线；校准用 ECE 等。
- **消融与校准分析**
  - 消融组件：去除 CfC、LNN 图驱动、LNN 稠密层、补偿机制、同时去除 CfC+LNN。

## 4. 资源与算力
- 文中没有提供具体的计算资源信息（GPU 型号、数量、训练时长、批次大小等均未提及）。

## 5. 实验数量与充分性
- 共进行了以下多组实验：
  - 五折交叉验证主数据集（单独展示各折指标）。
  - 与 PIPR、SWING 在同测试集比较。
  - 高度不平衡数据集上对比 RF2‑PPI。
  - 在不平衡训练条件下重训练并五折评估。
  - 酵母跨物种泛化五折实验。
  - 五项消融实验（含横向雷达图和贡献百分比分析）。
  - 四种校准方法的五折比较（含 ECE 热图）。
  - 三个生物案例（FGF23‑Klotho 复合物、SHP2 信号底物、Tdk1 寡聚态）。
  - TPR 靶点为中心的实验验证（免疫印迹、co‑IP）。
- 实验设计比较全面，覆盖了平衡/不平衡、跨物种、消融、校准、生物意义和实验验证，评估客观公平，且提供了详细的统计信息。

## 6. 主要结论与发现
- LNGCN 在主平衡测试集上 AUPRC 0.9823，AUROC 0.9829，MCC 0.8936，显著优于 PIPR 和 SWING。
- 在 1:10 高度不平衡场景中，AUPRC 0.8935（对比 RF2‑PPI 的 0.4073），保持高召回率（0.9424），适合保留真实互作。
- 酵母跨物种 AUPRC 0.9372，AUROC 0.9352，展现出泛化能力。
- 消融实验证实 CfC 和 LNN 模块均为关键贡献，图驱动 LNN 模块贡献最大。
- 分层集成校准有效降低 ECE，使分数更接近真实经验分布。
- 生物案例表明校准分数能在复杂组装、信号通路和寡聚状态中给出机制一致、可解释的优先排序。
- 实验验证：LNGCN 从质谱候选物中恢复已知的 NUP153‑TPR 和 GANP‑TPR 互作，并优先化了 ELAVL1‑TPR、RALY‑TPR，经 co‑IP 证实为物理互作，而 RF2‑PPI 给出低分。
- LNGCN 可作为从大规模候选列表到可测试假设的实用优先化工具。

## 7. 优点
- **距离感知连续时间图演化**：以残基径向距离显式驱动节点状态演化，克服离散图层对空间层级的抹平，抑制过平滑。
- **CfC 特征压缩保留空间信息**：高效去噪同时保持径向距离信号。
- **对称融合与 LNN 稠密分类**：保证输入顺序无关，并利用连续动态分类。
- **高质量校准**：四方法层次集成，提供可解释的概率，适合直接用于实验优先级设定。
- **全面的实验验证**：覆盖平衡/不平衡、跨物种、消融、校准，以及湿实验验证，证据链完整。
- **生物学意义导向**：在多个信号系统和复合物中展示机制一致性，不单纯追求分类指标。

## 8. 不足与局限
- **模型仅限二元互作预测**，未显式考虑翻译后修饰、亚细胞定位、疾病条件等上下文因素。
- **跨物种验证仅限于酵母**，对其他模式生物和更远物种的泛化性未经验证。
- **输入为静态 AlphaFold 结构**，不能直接利用构象动态（如分子动力学轨迹），无法建模构象调控的互作。
- **校准集规模有限（3000）**，且负样本构建可能未完全排除所有未发现的互作，存在一定偏差风险。
- **计算成本未量化**：缺乏与轻量级方法的推理时间和显存比较，不利于工程部署评估。
- **没有与最新的一些结构‑图 PPI 方法（如 DSCRIPT、GNN‑PPI 等）进行系统性比较**，缺少与纯序列模型或大规模语言模型的横向基准。
- **依赖 STRING 数据库标记正样本**，可能引入已知知识偏差；对于新发现的互作类型（如非经典结合模式）可能不准。
- **LNN 图演化的训练效率、超参数敏感性和可扩展性未作深入分析**。

（完）
