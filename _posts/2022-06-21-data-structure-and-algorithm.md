---
layout: post
title: "Data Structure and Algorithm"
categories: DSA
---

# 贪心算法

- 思想：选择每一阶段的局部最优，从而达到全局最优。
- 难点：如何通过局部最优，推出整体最优。
- 验证：手动模拟或举反例判断是否可以用贪心。

### 解题步骤

- 将问题分解为若干个子问题
- 找出适合的贪心策略
- 求解每一个子问题的最优解
- 将局部最优解堆叠成全局最优解

### 题目

[455. 分发饼干](https://leetcode.cn/problems/assign-cookies/)

- 思路：优先以较小尺寸的饼干满足较小胃口值的孩子

- 实现：将孩子胃口值 `g[i]` 和饼干尺寸 `s[j]` **升序**排列，遍历每个饼干，**优先满足胃口小的孩子**，若当前孩子得到满足，则考察下一个孩子，直至用尽所有饼干 或 满足所有孩子。

[377. 摆动序列](https://leetcode.cn/problems/wiggle-subsequence/)

- 思路：保留沿途上的**极值点**作为摆动序列元素

- 实现：使用变量 `prediff` 表示上一状态两个元素之间的差值，`curdiff` 表示当前两个元素之间的差值，当 `prediff` 和 `curdiff` 异号时，表示遇到了一个极值点，元素数量加一，并更新 `prediff`的状态。

[53. 最大子序和](https://leetcode.cn/problems/maximum-subarray/)

- 思路：使用非负子序和去更新最大子序和

- 实现：遍历数组中的元素，将其加到 `cursub` 中，并以此更新 `maxsub`。如若 `cursub < 0`，就将其置零，使得新的子序和从 `0` 开始累加，而非原本的负值。

[122. 买卖股票的最佳时机II](https://leetcode.cn/problems/best-time-to-buy-and-sell-stock-ii/)

- 思路：累加相邻两天的正利润

- 实现：将股票的交易利润进行分解。遍历股票价格，计算前后两天的交易利润，累加**大于0**的利润。

[55. 跳跃游戏](https://leetcode.cn/problems/jump-game/)

- 思路：最大跳跃距离是否能覆盖数组最后一个位置

- 实现：维护一个最远跳跃距离 `maxjump`，遍历数组`[0, maxjump]`，不断更新 `maxjump`。若 `maxjump` 覆盖最后一个位置，则返回 `true`。

[45. 跳跃游戏II](https://leetcode.cn/problems/jump-game-ii/)

- 思路：每一步尽可能跳远一些

- 实现：维护最远跳跃距离 `maxjump` 和 当前跳跃距离 `curjump`，遍历数组`[0,n-2]`，不断更新 `maxjump`，若访问到 `curjump` 的位置，则增加跳跃次数，并使用 `maxjump` 更新 `curjump`。

[1005. K次取反后最大化的数组和](https://leetcode.cn/problems/maximize-sum-of-array-after-k-negations/)

- 思路：优先取反绝对值较大的负数

- 实现：对数组以绝对值大小升序排列，逆序遍历整个数组，遇到负数且 `K > 0` 时就将负数取反并 `--K`。退出循环后若 `K` 为奇数，就将数组的首元素取反一次。

[134. 加油站](https://leetcode.cn/problems/gas-station/)

- 思路：当前剩余油量小于零时更新起始加油站编号

- 实现：使用变量 `totalrest` 和 `currest` 表示总/当前剩油量，剩油量由 `gas[i] - cost[i]` 表示。遍历所有加油站，不断更新 `totalrest` 和 `currest`，若 `currest < 0`，则将 `currest` 置零 并 将下一个加油站作为起始加油站。退出循环后，若 `totalrest < 0`，说明不能走完整个路程。

[135. 分发糖果](https://leetcode.cn/problems/candy/)

- 思路：分别正序及逆序根据评分及糖果数分发糖果

- 实现：使用长度为 `n` 且初值为 `1` 的数组记录每个孩子的糖果数，先正序遍历数组，使相邻孩子中评分高的糖果数再多出一个；再逆序遍历数组，使相邻孩子中评分高且糖果少的，糖果数再多出一个。

[860. 柠檬水找零](https://leetcode.cn/problems/lemonade-change/)

- 思路：尽可能使用10美元的零钱而保留5美元的零钱

- 实现：使用变量 `five`、`ten` 及 `twenty` 分别表示三种零钱的数量。遍历整个数组，更新5美元和10美元零钱数，当收到20美元的账单时，尽可能使用10美元零钱去找零。

[406. 根据身高重建队列](https://leetcode.cn/problems/queue-reconstruction-by-height/)

- 思路：优先将身高较高且编号较小的人插入队列

- 实现：对数组根据身高较高且编号较小的顺序进行排序，构造`list<vetor<int>>`队列，遍历整个数组，根据编号将队员插入队列中。

[452. 用最少数量的箭引爆气球](https://leetcode.cn/problems/minimum-number-of-arrows-to-burst-balloons/)

- 思路：根据气球右边界判定重叠范围

- 实现：根据气球的右边界对数组升序排列，使用变量 `cover` 表示气球覆盖范围的右边界，遍历数组`[1,n-1]`，若当前气球的左边界大于 `cover`，则更新 `cover` 并 增加弓箭数。

[435. 无重叠区间](https://leetcode.cn/problems/non-overlapping-intervals/)

- 思路：根据区间右边界判定重叠范围

- 实现：根据区间的右边界对数组升序排列，使用变量 `prev` 表示上一区间的右边界，遍历数组`[1,n-1]`，若当前区间的左边界小于 `prev`，则增加区间移除数；否则更新 `prev`。

[763.划分字母区间](https://leetcode.cn/problems/partition-labels/)

- 思路：根据字母最后出现的位置划分区间

- 实现：保存字符串 `S` 中每个字母最后出现的位置，使用变量 `begin` 和 `end` 表示区间的左/右边界，遍历 `S`，不断更新 `end`。若当前索引抵达 `end`，则记录此区间，并更新 `begin`。

[56. 合并区间](https://leetcode.cn/problems/merge-intervals/)

- 思路：根据区间左边界排序后动态更新重叠区间

- 实现：根据区间的左边界对数组升序排列，使用二维数组 `ret` 表示所有重叠区间，遍历数组`[1,n-1]`，若当前区间的左边界大于 `ret` 末区间的右边界，则将此区间添加到 `ret` 中；否则更新 `ret` 末区间的右边界为两个右区间的较大者。

[738. 单调递增的数字](https://leetcode.cn/problems/monotone-increasing-digits/)

- 思路：逆序地保证数组前后位数数字递增

- 实现：使用 `flag` 记录起始修改位置，逆序遍历数字中的每一位，若当前数字大于下一位数字，则将当前数字减一，并更新 `flag` 为下一位数字的索引。退出循环后，将从 `flag` （包含）位置以后的数字修改为 `9`。

[714. 买卖股票的最佳时机含手续费](https://leetcode.cn/problems/best-time-to-buy-and-sell-stock-with-transaction-fee/)

- 思路：累加当前股价与当前最低股价+手续费之间的正利润

- 实现：使用变量 `minprice` 表示当前最低股价，遍历数组`[1,n-1]`，不断更新 `minprice`，若当前股价大于 `minprice + fee`，则累加当前利润，并更新 `minprice`（免去手续费）。