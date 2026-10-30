# contrastive_learning_student_teacher_model
对比学习文献&amp;蒸馏模型文献_学习记录


蒸馏关键模型发展历史线：
｜时间｜代表工作 ｜主要贡献｜
|---|---:|---:|
｜2006｜Model Compression ｜ 用集成模型的输出训练一个紧凑模型，是现代知识蒸馏的重要前身｜
｜2015 ｜ Knowledge Distillation（Hinton）｜ 系统推广 Teacher-Student 知识蒸馏，利用软标签传递知识｜
｜2017 ｜	Mean Teacher	｜ 使用 Student 参数的 EMA 构造 Teacher，用于半监督学习｜
｜2018 ｜Born Again Networks（BAN） ｜	探索同规模模型之间的自蒸馏｜
｜2020 ｜	BYOL	｜ 无标签、无负样本的自监督表征学习，使用 EMA Target Network｜
｜2021 ｜	DINO	｜ 明确提出无标签自蒸馏（Self-Distillation with No Labels），并展示 ViT 的优秀特征能力｜

参考原始论文：
- 2015：[Distilling the Knowledge in a Neural Network](https://arxiv.org/pdf/1503.02531)
- 2017：[Mean Teachers Are Better Role Models](https://arxiv.org/pdf/1703.01780)
- 2018：[Born Again Neural Networks](https://arxiv.org/pdf/1805.04770)
- 2020：[Bootstrap Your Own Latent (BYOL)](https://arxiv.org/pdf/2006.07733)
- 2021：[Emerging Properties in Self-Supervised Vision Transformers (DINO)](https://arxiv.org/pdf/2104.14294)

从有监督->半监督->无监督，从输出一个类别->特征向量->概率分布，从卷积cnn网络到viT过渡。蒸馏代表整个架构中会存在两个特征提取网络，如果是不同构有知识浓缩意味。如果是同架构就是自蒸馏，感觉是像同一个规模的数据用double倍参数去学习特征。一般作为某个任务的前序模型。

对比学习关键模型：
｜论文	｜ 年份／会议 ｜主要功效｜
|---|---:|---:|
｜SimCLR — A Simple Framework for Contrastive Learning of Visual Representations	｜ ICML 2020	｜ 如何把研究问题落到数据增强、投影头和训练策略，再用消融支撑贡献。适合学习摘要中“方法发现—定量结果”的组织。｜
｜BYOL — Bootstrap Your Own Latent: A New Approach to Self-Supervised Learning	｜ NeurIPS 2020｜	在线网络预测目标网络的表征，目标网络通过移动平均更新。重点学习如何用简洁语言交代学习目标和两个分支的关系。｜
｜DINO — Emerging Properties in Self-Supervised Vision Transformers	｜ ICCV 2021	｜如何围绕“自监督表征呈现哪些性质”组织论文，并用分割相关特征、近邻分类等证据说明表征能力。尤其值得读摘要和引言。｜
｜SimSiam — Exploring Simple Siamese Representation Learning	｜ CVPR 2021	｜如何围绕一个明确问题展开：简单孪生网络为何能学习有效表征，停止梯度起什么作用。适合学习问题驱动的实验与论证。｜
｜VICReg — Variance-Invariance-Covariance Regularization for Self-Supervised Learning	｜ ICLR 2022	｜ 如何解释一致性、维度方差与去相关各自解决的问题。与你的方法中保持稳定性、避免坍塌和冗余直接相关。｜
｜Barlow Twins — Self-Supervised Learning via Redundancy Reduction	｜ ICML 2021	｜ 如何用“减少冗余”这一清晰原则统一方法叙述，避免把论文写成损失项清单。｜
｜DINOv2 — Learning Robust Visual Features without Supervision	｜ 2023 预印本	｜ 如何通过多个任务和数据分布验证冻结特征的通用性。适合借鉴评价组织，但其大规模训练定位与你的小样本材料任务不同。｜
