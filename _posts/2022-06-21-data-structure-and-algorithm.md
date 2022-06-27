---
layout: post
title: "Data Structure and Algorithm"
categories: DSA
---

# 1. 贪心算法

- 思想：选择每一阶段的局部最优，从而达到全局最优。
- 难点：如何通过局部最优，推出整体最优。
- 验证：手动模拟或举反例判断是否可以用贪心。

## 解题步骤

- 将问题分解为若干个子问题
- 找出适合的贪心策略
- 求解每一个子问题的最优解
- 将局部最优解堆叠成全局最优解

## 题目

[455. 分发饼干](https://leetcode-cn.com/problems/assign-cookies/)

思路：将孩子胃口值 `g[i]` 和饼干尺寸 `s[j]` **升序**排列，枚举每个饼干，**优先满足胃口小的孩子**，若 当前孩子得到满足，则考察下一个孩子，直至用尽所有饼干 或 满足所有孩子。

[377. 摆动序列](https://leetcode-cn.com/problems/wiggle-subsequence/)

思路：保留沿途上的**极值点**作为摆动序列元素。`prediff` 表示上一状态两个元素之间的差值，`curdiff` 表示当前两个元素之间的差值，当 `prediff` 和 `curdiff` 异号时，表示遇到了一个极值点，并更新 `prediff`的状态。

[53. 最大子序和](https://leetcode-cn.com/problems/maximum-subarray/)

思路：枚举数组中的元素，将其加到 `cursub` 中，并以此更新 `maxsub`。如若 `cursub < 0`，就将其置零，使得新的子序和从 `0` 开始累加，而非原本的负值。

[122. 买卖股票的最佳时机II](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-ii/)

思路：将股票的交易利润进行分解。枚举股票价格，计算前后两天的交易利润，累加**有盈利**的交易利润。