---
layout: post
title: "Solution of DSA in Interview "
categories: leetcode
toc: true
---

# 算法 - Algorithms
- 排序算法：快速排序、归并排序、计数排序
- 搜索算法：回溯、递归、剪枝技巧
- 图论：最短路、最小生成树、网络流建模
- 动态规划：背包问题、最长子序列、计数问题
- 基础技巧：分治、倍增、二分、贪心

# 数据结构 - Data Structures
- 数组与链表：单 / 双向链表、跳舞链
- 栈与队列
- 树与图：最近公共祖先、并查集
- 哈希表
- 堆：大 / 小根堆、可并堆
- 字符串：字典树、后缀树

# 题目

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