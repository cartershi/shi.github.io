---
title: "A FACTOR 2 APPROXIMATION ALGORITHM FOR THE GENERALIZED STEINER NETWORK PROBLEM"
date: 2019-07-22T16:45:33+08:00
draft: true
tags: ["论文学习"]
---

作者：Kamal Jain

## Introduction

本文的目标是找到一个子图使得给定目标之间的割满足条件。

f is weakly supermodular, i.e., it satisfies:
1. f(V)=0
2. For every A,B⊆V , at least one of the following holds
   1. $f(A)+f(B)\le f(A-B)+f(B-A)$
   2. $f(A)+f(B)\le f(A\cap B)+f(A\cup B)$

## Preliminaries

**Definition 2.1** function f : $2^V \rightarrow Z_+$is proper if f(V) = 0 and the following two conditions hold

1. For every subset S of V , f(S)=f(V−S).
2. For all disjoint subsets A and B of V , f(A∪B)≤max{f(A),f(B)}

可证明proper函数是weakly supermodular的。

**Definition 2.3** A function f :  $2^V \rightarrow Z_+$is submodular if f(V) = 0 and for every two sets A,B⊆V , the following two conditions hold

   1. $f(A)+f(B)\ge f(A-B)+f(B-A)$
   2. $f(A)+f(B)\ge f(A\cap B)+f(A\cup B)$

这里的submodular显然是与supermodular相反的，wearkly就是这两个条件只需要满足一个。

可证明$|\delta_B(.)|$是sunmodular。

**Theorem 2.5** x为G的子图，f : $2^V \rightarrow Z_+$是weakly supermodular function，则$f(S)-\delta_x(S)$是weakly supermodular function。用上面的结论即可。

## A factor of 2 approximation algorithm

在LP解出的所有$\ge\frac{1}{2}$的所有边形成的子图x中求$\delta_x(S)$，则由定理2.5，在去掉s后图中进行LP，限制1依然是weakly supermodular，所以形式完全一样，这样可以递归处理这个问题。于是由于原问题的最优解去除所有$\ge\frac{1}{2}$的所有边的贡献后的结果必然比子问题的最优解大，所以很自然可以推出定理3.2。这样就能得到一个2近似的算法， Iterative Rounding。
