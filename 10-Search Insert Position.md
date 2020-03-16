我用JS刷LeetCode | Day 10 |  Search Insert Position
###  搜索插入位置:

> 说明：现阶段的解题暂未考虑复杂度问题

首发地址：[http://www.brandhuang.com/article/1584366828427](http://www.brandhuang.com/article/1584366828427)

### Question：
Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You may assume no duplicates in the array.


### 中文题目：

给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。

你可以假设数组中无重复元素。

Example:

```javascript
Input: [1,3,5,6], 5
Output: 2

Input: [1,3,5,6], 2
Output: 1

Input: [1,3,5,6], 7
Output: 4

Input: [1,3,5,6], 0
Output: 0
```

### 个人分析：
1. 读完题目我们可以得到的信息：`「排序数组」`,`返回目标值在数组中的索引`，`数组中元素不重复`。
2. 我们只需要 `遍历数组，将每个元素和目标值相比，当数组中元素第一次大于或者等于目标值时，说明目标值在数组中的位置就是该元素现在的位置`.
3. 于是得到答案。 


### Answer：

```js
var searchInsert = function(nums, target) {
    for (var i = 0; i < nums.length; i++) {
       if (nums[i] >= target) {
           return i
       }
    }
    return nums.length
};
```

### 说明
发现最近的题开始需要有一点数据结构的知识了，所以刷题的速度会放慢，需要去补充下数据结构的知识。

之前在博客发了两篇，可以看看：

[JavaScript版数据结构与算法——基础篇（一）](http://www.brandhuang.com/article/1575117792236)

[JavaScript版数据结构与算法——基础篇（二）](http://www.brandhuang.com/article/1575180328471)

### 其他：

本题更多 `JavaScript` 解析，点击链接访问对应的答案：[https://leetcode.com](https://leetcode.com/problems/search-insert-position/discuss/?currentPage=1&orderBy=most_relevant&query=javascript)


