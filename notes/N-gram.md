# Application of MLE in N-gram theorm

![image](https://github.com/huskydoge/CS3602-NLP/assets/91367324/c20c4a48-5001-4b41-8d64-0addabbf8109)

## N-gram概率计算方法

N - gram模型的的参数（即概率值 $\left.P\left(w_k \mid w_{k-1}, \cdots, w_{k-(n-1)}\right)\right)$ 是通过最大似然估计法计算出 来的具体计算过程在这一部分的最后给出, 这里仅给出结论:

$$P\left(w_k \mid w_{k-1}, \cdots, w_{k-(n-1)}\right)=\frac{c\left(w_k, w_{k-1}, \cdots, w_{k-(n-1)}\right)}{c\left(w_{k-1}, \cdots, w_{k-(n-1)}\right)}$$

$c(\cdot)$ 表示 . 在训练预料中出现的次数。
即在给定 $w_{k-1}, \cdots, w_{k-(n-1)}$ 的条件下 $w_k$ 出现给定概率为：训练预料中序列 $w_{k-1}, \cdots, w_{k-(n-1)}$ 出现的个数 $\div$ 序列 $w_k, w_{k-1}, \cdots, w_{k-(n-1)}$ 出现的个数.

## 最大似然估计法
假设训练预料为 $W_1^N=\[w_1, \cdots, w_N\]$, 可以理解为输入的一个句子。

我们要估计的参数为: $P\(w_k \mid W_{k-n+1}^{k-1}\), w \in V$，即我们要让给定 $W_{k-n+1}^{k-1}\), w \in V$ 的时候，其下一个词是 $w_k$ 的概率最大。

其中 $V=\[v_1, \cdots, v_M\]$ 为词表。

**Criterion:**

$$
\begin{aligned}
\mathcal{L}(\theta) & =\frac{1}{K} \sum_{k=1}^K \log P\left(w_k \mid W_{k-n+1}^{k-1}\right) \\
& =\frac{1}{K} \sum_{v \in \mathcal{V}} \sum_{y \in \mathcal{Y}} \sum_{k: w_k=v, y=W_{k-n+1}^{k-1}} \log P(v \mid y) \\
& =\frac{1}{K} \sum_{v \in \mathcal{V}} \sum_{y \in \mathcal{Y}} C(y, v) \log P(v \mid y)
\end{aligned}
$$

其中 $\mathcal{Y}$ 是所有可能的 $n$-gram 历史的集合, $C(y, v)$ 是训练集中完 整 $n$-gram $(y, v)$ 的数目, $K$ 的意思是在这个训练句子中长度为n的窗口的可能的个数。
