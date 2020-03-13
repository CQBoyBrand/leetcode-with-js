我用JS刷LeetCode | Day 9 |  Implement strStr()
### 删除排序数组中的重复项:

> 说明：现阶段的解题暂未考虑复杂度问题

首发地址：[http://www.brandhuang.com/article/1584100918664](http://www.brandhuang.com/article/1584100918664)

### Question：
Implement strStr().

Return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

**Clarification:**

What should we return when needle is an empty string? This is a great question to ask during an interview.

For the purpose of this problem, we will return 0 when needle is an empty string. This is consistent to C's strstr() and Java's indexOf().

### 中文题目：

实现 strStr() 函数。

给定一个 `haystack` 字符串和一个 `needle` 字符串，在 `haystack` 字符串中找出 `needle` 字符串出现的第一个位置 (从 `0` 开始)。如果不存在，则返回  `-1`。

说明:

当 needle 是空字符串时，我们应当返回什么值呢？这是一个在面试中很好的问题。

对于本题而言，当 needle 是空字符串时我们应当返回 0 。这与C语言的 strstr() 以及 Java的 indexOf() 定义相符。

Example:

```javascript
Input: haystack = "hello", needle = "ll"
Output: 2

Input: haystack = "aaaaa", needle = "bba"
Output: -1
```

### 个人分析：
1. 看到题目第一想法， 可以使用 `indexOf`，于是得到 `答案一`。
2. 分享几个其他答案:`你有想到将输入的 haystack 以 needle 为分隔符，转换成字符串吗？转换成的数组的第一个元素的长度，就是我们需要的找的字符串出现的第一个位置 `，于是得到 `答案二`.
3. 当 `needle` 和 `haystack` 相等，或者 `needle` 为空，则直接返回 `0`。然后 `遍历 haystack`, 当 `haystack` 中出现某个元素与 `needle` 中第一个元素相等时，利用 `substring 方法`，从当前元素开始，在 `haystack`中截取 `neddle 长度`的字符串，比较截取的值是否和 `needle` 相等，若相等，`当前元素的索引即为所求的值`，否则返回 `-1`，于是得到 `答案三`。  



### Answer：

```js
// 答案一
var strStr = function(haystack, needle) {
     return haystack.indexOf(needle)
};

//答案二
var strStr = function(haystack, needle) {
    if (needle === '') return 0;
    const split = haystack.split(needle);
    return split.length > 1 ? split[0].length : -1;
};

// 答案三
var strStr = function(haystack, needle) {
    if (haystack === needle || needle === "") {
        return 0;
    }
    for (let i = 0; i < haystack.length; i++) {
        if (haystack[i] === needle[0]) {
            let temp = haystack.substring(i, i + needle.length);
            if (temp === needle) {
                return i;
            }
        }
    }
    return -1;
};
```



### 其他：

本题更多 `JavaScript` 解析，点击链接访问对应的答案：[https://leetcode.com](https://leetcode.com/problems/implement-strstr/discuss/?currentPage=1&orderBy=most_relevant&query=javascript)


