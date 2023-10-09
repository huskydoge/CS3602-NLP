# Hidden Markov Model

一个概率模型

`part-of-speech tagging`

## 一阶关联
`NNP - > NNP`, `MD -> VB`

* 可以用一个矩阵来表达

## 二阶关联
`CD -> NNS/NN -> JJ`


* 我们只知道单词（v），不知道背后的词性（h）
* 我们知道词性之间组织起来的规则
* **认为下一个h只跟前面一个h有关**（马尔可夫假设）


$$p(h|v) = \frac{p(v|h) p(h)}{p(v)}$$


$$P(h_1,h_2,\cdots,h_i,\cdots,h_n) = p(h_1) \cdot \prod_{i=1}^{n - 1} P(h_{i+1} | h_{i})$$


概率太小，取log防止浮点溢出

## Viterbi算法

