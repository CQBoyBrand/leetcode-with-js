我用JS刷LeetCode | Day 1 | Two Sum

### 两数之和：
> 说明：现阶段的解题暂未考虑复杂度问题

首发地址：[http://www.brandhuang.com/article/1583315258879](http://www.brandhuang.com/article/1583315258879)

### Question：

Given an array of integers, return `indices` of the two numbers such that they add up to a specific target.

You may assume that each input would have `exactly` one solution, and you may not use the same element twice.

中文题目：

给定一个整数数组 `nums` 和一个目标值 `target`，请你在该数组中找出和为目标值的那两个整数，并返回他们的数组下标。

你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。

Example:

```js
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```



### 个人分析：

1. 由题目「 你不能重复利用这个数组中同样的元素 」 可以知道，这个数组中的元素是不重复的。
2. 「可以假设每种输入只会对应一个答案」，说明不需要考虑类似 [0, 1] 和 [1, 0] 这样的问题。
3. 两个整数的和为 `target`，所以可以用可以用其中一个数（暂且称为 A）和 `target` 的表达式来表示另一个数（称为 B， B = target - A）。
4. 利用 `Object` 中 `key` 的唯一性，先遍历 `nums` 数组， 每次遍历，A 和 B 都会发生变化。
5. 如果在 `Object` 中，以 B 为 `key` 值的 `value` 不存在， 将 B 作为 `Object` 的 `key`, B 对应的索引当作 `value`。
6. 如果在 `Object` 中，以 B 为 `key` 值的 `value` 存在，则此时 A 的索引和以 B 为 `key` 的 `value` 值， 即为所求结果。
7. 得出如下答案。




### Answer：

```js
var twoSum = function(nums, target) {
    var res = {}
    for (var i = 0; i < nums.length; i++) {
        var other = target - nums[i]
        if (res[other] !== undefined) {
            return [res[other] , i]
        } else {
            res[nums[i]] = i
        }
    }
    return []
};

```



### 其他：

这道题之前在其他地方见过，当时使用的暴力破解法：两个 `for` 循环嵌套

```js
var twoSum = function(nums, target) {
    for (var i = 0; i < nums.length; i++) {
        for (var j = i + 1; j < nums.length; j++) {
            if (nums[i] + nums[j] === target) {
                return [i, j]
            }
        }
    }
}
```

本题更多 `JavaScript` 解析，点击链接访问对应的答案：[https://leetcode.com](https://leetcode.com/problems/two-sum/discuss/?currentPage=1&orderBy=most_relevant&query=javascript)


