我用JS刷LeetCode | Day 8 |  Remove Duplicates from Sorted Array
### 删除排序数组中的重复项:

> 说明：现阶段的解题暂未考虑复杂度问题

首发地址：[http://www.brandhuang.com/article/1584012985173](http://www.brandhuang.com/article/1584012985173)

### Question：
Given an array nums and a value val, remove all instances of that value in-place and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

The order of elements can be changed. It doesn't matter what you leave beyond the new length.

### 中文题目：

给你一个数组 `nums` 和一个值 `val`，你需要 原地 移除所有数值等于 `val` 的元素，并返回移除后数组的新长度。

不要使用额外的数组空间，你必须仅使用 `O(1)` 额外空间并 原地 修改输入数组。

元素的顺序可以改变。你不需要考虑数组中超出新长度后面的元素。

Example:

```javascript

给定 nums = [3,2,2,3], val = 3,

函数应该返回新的长度 2, 并且 nums 中的前两个元素均为 2。

你不需要考虑数组中超出新长度后面的元素。


给定 nums = [0,1,2,2,3,0,4,2], val = 2,

函数应该返回新的长度 5, 并且 nums 中的前五个元素为 0, 1, 3, 0, 4。

注意这五个元素可为任意顺序。

你不需要考虑数组中超出新长度后面的元素。
```

### 个人分析：
1. 和昨天那道题目一样，题目限制条件：`「不要使用额外的数组空间，你必须在原地修改输入数组」`。
2. 首先想到的方法很简单，直接 `遍历数组，若数组中元素与给定值相等，则直接使用 splice 方法删除，因为数组长度减少了一个，所以遍历的序号需要减一`，得到如下答案。



### Answer：

```js
var removeElement = function(nums, val) {
    for (let i = 0; i< nums.length; i++) {
        if (nums[i] == val) {
            nums.splice(i, 1)
            i--
        }
    }
    return nums.length
};
```



### 其他：

本题更多 `JavaScript` 解析，点击链接访问对应的答案：[https://leetcode.com](https://leetcode.com/problems/remove-element/discuss/?currentPage=1&orderBy=most_relevant&query=JavaScript)


