我用JS刷LeetCode | Day 4 | Longest Common Prefix
### 最长公共前缀:

> 说明：现阶段的解题暂未考虑复杂度问题

首发地址：[http://www.brandhuang.com/article/1583633108602](http://www.brandhuang.com/article/1583633108602)

### Question：
Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string `""`.

Note:

All given inputs are in lowercase letters a-z.

### 中文题目：

编写一个函数来查找字符串数组中的最长公共前缀。

如果不存在公共前缀，返回空字符串 ""。

注意：

所有输入只包含小写字母 a-z 。

Example:

```javascript

Input: ["flower","flow","flight"]
Output: "fl"

Input: ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.

```

### 个人分析：

1. 「公共」，说明是数组中的每个元素所共有的，「前缀」，说明从元素的左边开始算起。
2. 先考虑特殊情况：`当数组为空时，直接返回空字符串`
3. 看到题目稍加思索，应该想到：`先比较数组中每个元素的第一位，如果都相同，则开始比较每个元素的第二位，依次类推；直到出现一个元素的某一位不在其他元素中都出现，此时返回这个元素之前的值`
4. 因为公共前缀是在在所有的元素中都存在的，所以我们可以`以第一个元素作为标记点，将他的每一位和其他元素的每一位进行比较`。
5. 如果第一个元素遍历完成还没出现不在其他元素中值，则直接返回第一个元素。
6. 得出如下答案。

### Answer：

```js
var longestCommonPrefix = function (strs) {
    if (strs.length === 0) return ''
    let tag = strs[0]
    for (let j = 0; j < tag.length; j++) {
        for (let i = 0; i < strs.length; i++) {
            if (strs[i][j] !== tag[j]) {
                return strs[i].slice(0, j);
            } 
        }
    }
    return tag

};
```



### 其他：

本题更多 `JavaScript` 解析，点击链接访问对应的答案：[https://leetcode.com](https://leetcode.com/problems/longest-common-prefix/discuss/?currentPage=1&orderBy=most_relevant&query=javascript)


