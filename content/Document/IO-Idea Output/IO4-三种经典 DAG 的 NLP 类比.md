> - [[PO1]**text classification baseline**](https://www.notion.so/PO1-text-classification-baseline-319bcf323f7c8048afccda23e221e3c7?pvs=21)

根据你的 **B-W8-DAY6** 任务要求，你需要为三种经典的 DAG 结构（Chain, Fork, Collider）编写 **NLP 类比**，并草绘出 **IMDB DAG v0**。

结合你目前正在进行的 **IMDB 文本分类 Baseline 项目**（TF-IDF + 逻辑回归），你应当在 Notion 或 README 中写入以下内容：

### 1. 三种经典 DAG 的 NLP 类比

你需要用一句话解释这些结构在 NLP 任务中是如何体现的：

- **Fork (分叉结构：$X \leftarrow Z \rightarrow Y$)**
    - **类比：** **电影主题/类型 ($Z$)** 同时影响了 **评论中的关键词 ($X$)** 和 **情感标签 ($Y$)**。
    - **例子：** “恐怖片”这一类型会使得评论中高频出现“害怕”、“惊悚”等词汇，同时也可能天然吸引特定情感倾向的观众给出好评。
- **Collider (对撞结构：$X \rightarrow Z \leftarrow Y$)**
    - **类比：** **数据选择偏差 (Selection Bias, $Z$)** 是由 **评论长度 ($X$)** 和 **情感极性 ($Y$)** 共同决定的。
    - **例子：** 只有那些“非常短但情感极其强烈”的评论才会被选入某个特定的精选集。如果你在这个子集上训练，模型会误以为长度和情感之间存在虚假相关。
- **Chain (链式结构：$X \rightarrow Z \rightarrow Y$)**
    - **类比：** **文本内容 ($X$)** 决定了用户的 **评分分数 ($Z$)**，而分数进一步决定了 **二分类标签 ($Y$)**。
    - **例子：** “这电影太烂了”这个文本生成了 1 分的评分，1 分的评分导致了“负面（Negative）”的标签。

### 2. 草绘 IMDB DAG v0

基于你的 Baseline 项目，你的初版因果图应该尝试解释为什么简单的 TF-IDF 模型会遇到瓶颈。建议画出包含以下节点的图：

- **$S$ (Sentiment/情感本质)**：你真正想捕捉的变量。
- **$T$ (Topic/电影主题)**：如导演、类型，可能产生虚假相关。
- **$W$ (Words/词向量/TF-IDF 特征)**：模型观察到的特征。
- **$Y$ (Label/情感标签)**：数据中的正负面标记。

**可能的路径描述：**

1. $S \rightarrow W$：真实的情感流向文字。
2. $S \rightarrow Y$：情感决定标签。
3. $T \rightarrow W$：电影主题（如“恐怖片”）引入了特定词汇（如“可怕”），这些词在统计上与负面情感相关，但在该语境下可能代表正面。
4. $T \rightarrow S$：特定主题可能自带某种情感基调。

### 3. 核心总结建议

在你的任务输出中，你应该强调：**目前的 Baseline（TF-IDF + LR）实际上是在假设所有的词汇（$W$）都是由情感（$S$）直接生成的，而忽略了主题（$T$）作为混杂因素通过 $T \rightarrow W$ 引入的噪声。**

这就是为什么你发现模型在处理“微妙表达”和“混合情感”时容易出错的原因——它无法区分一个词究竟是因为“情感”而出现，还是因为“电影背景”而出现。

---

```MERMAID
graph LR
T[Topic] --> X[Text]
T --> Y[Label]
S[Spurious] --> X
X --> Z[Rep]
Z --> Yhat[Prediction]
E[Environment] --> X
E --> S
```
