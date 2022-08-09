---
layout: post
title: "Solution of DSA in Interview "
categories: leetcode
toc: true
---

# 数据结构 - Data Structures
- 数组与链表：单 / 双向链表、跳舞链
- 栈与队列
- 树与图：最近公共祖先、并查集
- 哈希表
- 堆：大 / 小根堆、可并堆
- 字符串：字典树、后缀树


# 算法 - Algorithms
- 排序算法：快速排序、归并排序、计数排序
- 搜索算法：回溯、递归、剪枝技巧
- 图论：最短路、最小生成树、网络流建模
- 动态规划：背包问题、最长子序列、计数问题
- 基础技巧：分治、倍增、二分、贪心

# 题目

## 开始之前

[136. 只出现一次的数字](https://leetcode.cn/problems/single-number/)

- 思路：使用「异或」运算

[169. 多数元素](https://leetcode.cn/problems/majority-element/)

- 思路：使用「打擂台」的方式更新候选元素

[240. 搜索二维矩阵 II](https://leetcode.cn/problems/search-a-2d-matrix-ii/)

- 思路：从右上角元素开始与 `target` 比较，判断向下移动或向右移动或返回结果。

[88. 合并两个有序数组](https://leetcode.cn/problems/merge-sorted-array/)

- 思路：双指针，倒序比较两数组中有效元素，并将较大者放入数组一的末尾。

[887. 鸡蛋掉落](https://leetcode.cn/problems/super-egg-drop/)

- 思路：hard

## 字符串

[125. 验证回文串](https://leetcode.cn/problems/valid-palindrome/)

- 思路：对撞指针，判断双指针当前指向的字母或数字字符是否相等。

[131. 分割回文串](https://leetcode.cn/problems/palindrome-partitioning/)

- 思路：回溯，判断 `s` 中以 `idx` 开始的每个子串是否是回文串，如是则添加到 `comb` 中。

[139. 单词拆分](https://leetcode.cn/problems/word-break/)

- 思路：动态规划，`dp[i]` 表示 `s` 中的前 `i` 个字符组成的字符串是否可以拆分为字典中的单词，`dp[i] = dp[j] && check(s[j...i-1])`。

[140. 单词拆分 II](https://leetcode.cn/problems/word-break-ii/)

- 思路：回溯，使用哈希表存储 `s` 中以索引 `i` 开始的子串组成的句子，判断每个子串是否出现在字典中，如出现则递归判断下一个子串。

[208. 实现 Trie (前缀树)](https://leetcode.cn/problems/implement-trie-prefix-tree/)

- 思路：每个节点包括一个 `vector<Trie*> children` 和一个 `bool isEnd`。

[212. 单词搜索 II](https://leetcode.cn/problems/word-search-ii/)

- 思路：回溯，在四个方向上判断当前字符是否与 `word` 中对象的字符相同，并更新 `visited`。

[242. 有效的字母异位词](https://leetcode.cn/problems/valid-anagram/)

- 思路：字母表或哈希表。

[387. 字符串中的第一个唯一字符](https://leetcode.cn/problems/first-unique-character-in-a-string/)

- 思路：哈希表，返回出现次数为1的字符。

[344. 反转字符串](https://leetcode.cn/problems/reverse-string/)

- 思路：对撞指针。

## 数组

[152. 乘积最大子数组](https://leetcode.cn/problems/maximum-product-subarray/)

- 思路：动态规划，`maxPrefix[i]` 表示以索引 `i` 结尾的子数组最大乘积，`minPrefix[i]`表示以索引 `i` 结尾的子数组最小乘积。

[169. 多数元素](https://leetcode.cn/problems/majority-element/)

- 思路：打擂台。

[189. 轮转数组](https://leetcode.cn/problems/rotate-array/)

- 思路：三次翻转。

[217. 存在重复元素](https://leetcode.cn/problems/contains-duplicate/)

- 思路：哈希表。

[283. 移动零](https://leetcode.cn/problems/move-zeroes/)

- 思路：双指针，将非零元素移动至开头并后移双指针。

[384. 打乱数组](https://leetcode.cn/problems/shuffle-an-array/)

- 思路：交换 `nums[i]` 和 `nums[i + rand() % (n-i)]` 实现打乱数组。

[350. 两个数组的交集 II](https://leetcode.cn/problems/intersection-of-two-arrays-ii/)

- 思路：哈希表，存储元素及其出现次数。

[334. 递增的三元子序列](https://leetcode.cn/problems/increasing-triplet-subsequence/)

- 思路：贪心，使得 `first` 及 `second` 较小使得更容易找到三元组。

[240. 搜索二维矩阵 II](https://leetcode.cn/problems/search-a-2d-matrix-ii/)

- 思路：双指针或者二分查找（将数组展平）。

[238. 除自身以外数组的乘积](https://leetcode.cn/problems/product-of-array-except-self/)

- 思路：一次遍历，每次计算索引 `i` 处的前缀积和 `n-i-1` 处的后缀积。

## 堆、栈与队列

[155. 最小栈](https://leetcode.cn/problems/min-stack/)

- 思路：维护两个栈，一个保存当前元素，一个保存当前最小元素。

[215. 数组中的第K个最大元素](https://leetcode.cn/problems/kth-largest-element-in-an-array/)

- 思路：最大堆排序或快速选择。

[295. 数据流的中位数](https://leetcode.cn/problems/find-median-from-data-stream/)

- 思路：使用两个优先级队列（小根堆和大根堆）模拟整个有序列表。

[378. 有序矩阵中第 K 小的元素](https://leetcode.cn/problems/kth-smallest-element-in-a-sorted-matrix/)

- 思路：使用优先级队列（小根堆）存储矩阵中的点，根据行索引搜索得到第k小的值。

[347. 前 K 个高频元素](https://leetcode.cn/problems/top-k-frequent-elements/)

- 思路：使用优先级队列（大根堆）存储 `pair<int, int>` 元素，记录每个元素出现的次数。

[239. 滑动窗口最大值](https://leetcode.cn/problems/sliding-window-maximum/)

- 思路：使用优先级队列（大根堆）保存当前窗口内的最大值及其在原数组内的索引。

[224. 基本计算器](https://leetcode.cn/problems/basic-calculator/)

- 思路：使用一个 `stack` 保存每个左括号前的符号，如遇正号则不变号，如符号则变号，如遇数字则乘以符号标志后加到结果中。

[227. 基本计算器 II](https://leetcode.cn/problems/basic-calculator-ii/)

- 思路：使用一个 `vector` 保存所有整数，使用 `preSign` 记录上一次出现的符号。根据符号的不同对当前整数进行不同处理。

[341. 扁平化嵌套列表迭代器](https://leetcode.cn/problems/flatten-nested-list-iterator/)

- 思路：使用一个 `stack` 逆序保存扁平化列表中的元素，对于 `hasNext()`：栈顶元素为整数时直接返回 `true`，为列表时则将其展平为元素并逆序放入栈中。

[150. 逆波兰表达式求值](https://leetcode.cn/problems/evaluate-reverse-polish-notation/)

- 思路：使用 `stack` 保存列表中的每个数，遇到符号时则依次弹出两个数进行计算并将结果再次压入栈中。

## 链表

[138. 复制带随机指针的链表](https://leetcode.cn/problems/copy-list-with-random-pointer/)

- 思路：使用哈希表存储旧表节点及其对应的新表节点，并依据旧表结点中的 `next` 和 `random` 构造新表节点中的对应 `next` 和 `random`。

[141. 环形链表](https://leetcode.cn/problems/linked-list-cycle/)

- 思路：快慢指针结合 `do...while()`。

[148. 排序链表](https://leetcode.cn/problems/sort-list/)

- 思路：归并排序，首先将原链表根据中点一分为二，并递归进行拆分操作，而后将子链表回溯合并即可。

[160. 相交链表](https://leetcode.cn/problems/intersection-of-two-linked-lists/)

- 思路：双指针，各自遍历 `list1 + list2`，相遇后即为首个相交节点。

[206. 反转链表](https://leetcode.cn/problems/reverse-linked-list/)

- 思路：更改`prev`、`curr`、`next`。

[234. 回文链表](https://leetcode.cn/problems/palindrome-linked-list/)

- 思路：翻转后半部分链表后，比较前后两部分子链表节点值是否一致。

[237. 删除链表中的节点](https://leetcode.cn/problems/delete-node-in-a-linked-list/)

- 思路：将后一节点前移覆盖当前节点，随后删除该后一节点。

[328. 奇偶链表](https://leetcode.cn/problems/odd-even-linked-list/)

- 思路：双指针，`odd->next = even->next`，`even->next = odd->next`。