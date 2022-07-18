---
layout: post
title: "Solution of Leetcode Contest"
categories: contest
toc: true
---

# Leetcode 周赛
## 第 302 场 (2022-07-17)

[6120. 数组能形成多少数对](https://leetcode.cn/problems/maximum-number-of-pairs-in-array/)

- 思路：使用哈希映射存储每个元素出现的次数

- 实现：使用一个 `unordered_map<int, int>` 存储每个元素出现的次数，则数对的个数为哈希映射中的value除以2的累积。

[6164. 数位和相等数对的最大和](https://leetcode.cn/problems/max-sum-of-a-pair-with-equal-sum-of-digits/)

- 思路：使用哈希映射存储每个数位和对应的元素

- 实现：使用一个哈希映射 `unordered_map<int, vector<int>>` 存储每个数位和对应的元素，则同一数位和对应不同的元素。遍历哈希映射，对每个 vector 类型的 value 进行降序排序，更新和的最大值。

[6121. 裁剪数字后查询第 K 小的数字](https://leetcode.cn/problems/query-kth-smallest-trimmed-number/)

- 思路：记录剪裁后的元素及其索引号并对齐进行排序

- 实现：遍历每一个query，使用 `vector<pair<string, int>>` 记录对原字符串剪裁后得到的字符串及其原索引，对此 vector 进行排序，保存 vector 中第 k 个 `pair` 的 `second`。