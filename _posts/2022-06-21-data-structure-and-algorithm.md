---
layout: post
title: "Data Structure and Algorithm"
categories: leetcode
toc: true
---

## 贪心算法

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

## 双指针

若两个指针指向同一数组
- 遍历方向相同且不会相交，则称为**滑动窗口**，经常用于区间搜索
- 遍历方向相反，则称为**对撞指针**，用于在有序数组中进行搜索

### 题目

[167. 两数之和 II - 输入有序数组](https://leetcode.cn/problems/two-sum-ii-input-array-is-sorted/)

- 思路：根据 `target` 的大小动态调整对撞指针的位置

- 实现：使用变量 `lo` 和 `hi` 表示数组中的对撞指针，当指针指向的元素之和小于 `target` 时，向右移动 `lo`；当指针指向的元素之和大于 `target` 时，向左移动 `hi`，直到和等于 `target`。

[88. 合并两个有序数组](https://leetcode.cn/problems/merge-sorted-array/)

- 思路：使用对比指针比较两个数组中的元素并逆序填充较大者

- 实现：使用两个指针分别逆序遍历两个数组中的元素，在第一个数组空白处逆序填入两指针指向元素的较大者。当出现遍历完一个数组的情况时，直接填入另一个数组中的元素即可。

[142. 环形链表 II](https://leetcode.cn/problems/linked-list-cycle-ii/)

- 思路：使用快慢指针从头节点开始向后移动直到相遇后的再次相遇

- 实现：初始时快慢指针同时指向链表的头节点，随后快指针每次向后移动两部，慢指针每次向后移动一步，直到两指针相遇。此时将快指针移至头节点，快慢指针各每次向后移动一步，直到两指针相遇，即为入环的第一个节点。

[76. 最小覆盖子串](https://leetcode.cn/problems/minimum-window-substring/)

- 思路：使用滑动窗口寻找有效的子串并比较出最短的

- 实现：首先将 `t` 中的所有字符存储到哈希映射中，然后在 `s` 中移动滑动窗口并将当前字符存储到另一哈希映射中，根据当前字符在两个哈希映射中的出现次数进行滑动窗口的移动，当 `s` 中有效字符数量和 `t` 字符串长度一致时，更新最短子串。

[633. 平方数之和](https://leetcode.cn/problems/sum-of-square-numbers/)

- 思路：不断移动对撞指针直至找到合适的整数

- 实现：初始时指针 `lo` 指向 0，指针 `hi` 指向 `sqrt(c)`。通过将平方和与 `c` 进行比较，判断左移 `lo` 或右移 `hi` 或返回结果。

[680. 验证回文字符串 II](https://leetcode.cn/problems/valid-palindrome-ii/)

- 思路：利用对撞指针判断字符是否相等

- 实现：使用指针 `lo` 和 `hi` 分别指向字符串的首位，依次判断字符是否相等。如相等则移动双指针；如不相等，则分别判断移动左右指针后的子字符串是否是回文串。

[524. 通过删除字母匹配到字典里最长单词](https://leetcode.cn/problems/longest-word-in-dictionary-through-deleting/)

- 思路：对字典自定义排序后利用双指针判断字符是否相等

- 实现：首先根据字符串长度和字母序对字典进行排序，随后将指针 `i`、`j` 分别指向字符串 `s` 和 排序后的字符串，判断两个串中的字符是否相等。如相等则同时移动 `i` 和 `j`，否则只移动`i`，此时如果 `j` 移动到了字符串末尾，则返回当前字典中的字符串。

[27. 移除元素](https://leetcode.cn/problems/remove-element/)

- 思路：使用双指针分别指向新数组和原数组

- 实现：使用变量 `idx` 表示新数组的索引，遍历整个数组，如果当前元素不等于 `val`，则将其放入新数组中，并后移 `idx`。

[344. 反转字符串](https://leetcode.cn/problems/reverse-string/)

- 思路：使用对撞指针依次交换字符串中的字符

- 实现：使用指针 `lo` 和 `hi` 分别指向字符串的首尾，每次交换指针所指向的字符，同时移动双指针。

[剑指 Offer 05. 替换空格](https://leetcode.cn/problems/ti-huan-kong-ge-lcof/)

- 思路：移动双指针填充扩容后的字符串

- 实现：首先根据空格的个数对原字符串进行扩容，然后使用指针 `i` 和 `j` 分别指向扩容后的字符串和原字符串的最后一个字符。当 `i > j` 时，遍历原字符串，如遇空格就向新字符串中逆序填充 `%20`，否则就填充当前字符。

[19. 删除链表的倒数第 N 个结点](https://leetcode.cn/problems/remove-nth-node-from-end-of-list/)

- 思路：利用双指针找到待删节点的前驱节点

- 实现：使用指针 `first` 指向 `head`，指针 `second` 指向 `dummy`。首先将 `first` 后移 `n` 次，然后同时后移 `first` 和 `second` 直至 `first` 为空，此时 `second` 便指向待删节点的前驱节点。

[面试题 02.07. 链表相交](https://leetcode.cn/problems/intersection-of-two-linked-lists-lcci/)

- 思路：移动双指针寻找链表交点

- 实现：使用指针 `pA` 和 `pB` 分别指向两个链表，如果 `pA` 或 `pB` 为空，则将其指向另一链表，否则后移该指针，直到两指针相遇。

[15. 三数之和](https://leetcode.cn/problems/3sum/)

- 思路：排序后固定第一个数的情况下使用对撞指针寻找另外两个数

- 实现：首先对数组进行升序排序，将数组的前n-2个元素之一作为三元组的第一个数，在余下子数组中利用对撞指针寻找另外两个数。

[18. 四数之和](https://leetcode.cn/problems/4sum/)

- 思路：排序后固定前两个数的情况下使用对撞指针寻找后两个数

- 实现：首先对数组进行升序排序，在数组的前n-3个元素中选两个作为四元组的前两个数，在余下子数组中利用对撞指针寻找后两个数。此题有多处剪枝操作，可大幅降低时间复杂度，同时需注意整数溢出问题。

## 二分查找

### 题目

[69. x的平方根](https://leetcode.cn/problems/sqrtx/)

- 思路：在 `0 ~ x` 中使用二分查找搜索 `k^2 <= x` 的最大 `k`

- 实现：令 `lo` 和 `hi` 分别指向 `0` 和 `x`，当 `lo <= hi` 时，若中位数的平方小于等于 `x`，则更新 `ret`，并向右半区间继续查找；否则，向左半区间继续查找。

[34. 在排序数组中查找元素的第一个和最后一个位置](https://leetcode.cn/problems/find-first-and-last-position-of-element-in-sorted-array/)

- 思路：使用二分查找分别搜索数组中该元素的第一个位置及该元素值+1的第一个位置

- 实现：使用 `fPos` 表示 `target` 的第一个出现位置， `lPos` 表示 `target + 1` 的出现位置-1。若  `fPos` 处的值合理则返回结果。

[33. 搜索旋转排序数组](https://leetcode.cn/problems/search-in-rotated-sorted-array/)

- 思路：在有序子数组中继续使用二分查找搜索目标值

- 实现：将中位数 `nums[mid]` 与首元素 `nums[lo]` 进行比较，若前半部分有序且目标值在其中，则深入前半部分继续查找；否则深入后半部分继续查找。

[81. 搜索旋转排序数组 II](https://leetcode.cn/problems/search-in-rotated-sorted-array-ii/)

- 思路：在有序子数组中继续使用二分查找搜索目标值

- 实现：将中位数 `nums[mid]` 与首元素 `nums[lo]` 进行比较，若 `nums[mid]` 与数组首位元素均相等，则前后各压缩一次数组；若前半部分有序且目标值在其中，则深入前半部分继续查找；否则深入后半部分继续查找。

[540. 有序数组中的单一元素](https://leetcode.cn/problems/single-element-in-a-sorted-array/)

- 思路：根据中位数的奇偶性进行相邻元素判断从而实现二分查找

- 实现：若 `mid` 为奇数，则将 `mid` 索引处的元素与上一元素相比；若 `mid` 为偶数，则将 `mid` 索引处的元素与下一元素相比；若比较的结果相等，则深入后半部分查找，否则深入前半部分继续查找。

[287. 寻找重复数](https://leetcode.cn/problems/find-the-duplicate-number/)

- 思路：根据不大于 `mid` 的元素数量进行二分查找

- 实现：使用 `cnt` 表示不大于 `mid` 的元素数量，若 `cnt <= mid` 则深入后半部分查找，否则深入前半部分继续查找。

[268. 丢失的数字](https://leetcode.cn/problems/missing-number/)

- 思路：总和减去元素和

- 实现：使用变量 `total` 表示 `[0, n]` 的总和，`sum` 表示数组 `nums` 中的元素和，则 `total - sum` 即为丢失的数字。

[222. 完全二叉树的节点个数](https://leetcode.cn/problems/count-complete-tree-nodes/)

- 思路：递归求取左子树和右子树上的节点数

- 实现：首先求取左子树和右子树上的层数，若二者相等，则左子树为满二叉树，返回左子树节点数并递归求取右子树；若二者不相等，则右子树为满二叉树，返回右子树节点数并递归求取左子树。

[4. 寻找两个正序数组的中位数](https://leetcode.cn/problems/median-of-two-sorted-arrays/)

- 思路：根据两数组总长度的奇偶性寻找数组第 `k` 个元素

- 实现：使用 `idx1` 和 `idx2` 表示两数组的起始索引，`newIdx1` 和 `newIdx2` 表示两数组第 `k/2` 个元素的索引。若 `newIdx1` 处的元素值不大于 `newIdx2` 处的元素值，则 `k` 减去 `newIdx1` 前的元素数，将 `idx1` 更新为 `newIdx1 + 1`；否则 `k` 减去 `newIdx2` 前的元素数，将 `idx2` 更新为 `newIdx2 + 1`。

## dfs/bfs

### dfs

深度优先搜索（depth-first seach，DFS）在搜索到一个新的节点时，立即对该新节点进行遍历；
因此遍历需要用先入后出的栈来实现，也可以通过与栈等价的递归来实现。

### bfs

广度优先搜索（breadth-first search，BFS）不同与深度优先搜索，它是一层层进行遍历的，因此需要用先入先出的队列而非先入后出的栈进行遍历。

由于是按层次进行遍历，广度优先搜索时
按照“广”的方向进行遍历的，也常常用来处理最短路径等问题。

## 回溯

回溯法（backtracking）是优先搜索的一种特殊情况，又称为试探法，常用于需要记录节点状态的深度优先搜索。
通常来说，排列、组合、选择类问题使用回溯法比较方便。

顾名思义，回溯法的核心是回溯。在搜索到某一节点的时候，如果我们发现目前的节点(及
其子节点)并不是需求目标时，我们回退到原来的节点继续搜索，并且把在目前节点修改的状态
还原。

## 动态规划

动态规划（Dynamic Programming，DP）在查找有很多
重叠子问题情况的最优解时有效。它将问题重新组合成子问题。

解决动态规划问题的关键是找到 **状态转移方程**，这样我们可以通过计算和储存子问题的解来求解最终问题。

## Others

[9. 回文数](https://leetcode.cn/problems/palindrome-number/)

- 思路：将原始数字进行翻转后与原数字进行对比
