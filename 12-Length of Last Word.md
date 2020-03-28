我用JS刷LeetCode | Day 12 |  Length of Last Word
###   最后一个单词的长度:

> 说明：现阶段的解题暂未考虑复杂度问题

首发地址：[http://www.brandhuang.com/article/1584966037919](http://www.brandhuang.com/article/1584966037919)

### Question：
给定一个仅包含大小写字母和空格 ' ' 的字符串 s，返回其最后一个单词的长度。如果字符串从左向右滚动显示，那么最后一个单词就是最后出现的单词。

如果不存在最后一个单词，请返回 0 。

说明：一个单词是指仅由字母组成、不包含任何空格字符的 最大子字符串。

Example:

```javascript
Input: "Hello World"
Output: 5
```

### 个人分析：
1. 分析题目：`最后一个单词的长度`,`单词，不包含任何空格字符`。
2. 我们知道，字符串中，单词之间是用空格来隔开的。所以我们容易想到，`将字符串以空格为分隔符，转换成数组，然后数组的最后一个元素的长度`就是我们所求的最后一个单词长度？你`仔细想想这其中于什么问题吗?`，如果你没发现什么问题，那么可能你会得到如下的`错误答案`。
3. 由`错误答案`进一步分析，如果给定的字符串是`以空格结尾的`，那么，我们从第 2 步得到的`最后一个元素将会是一个空字符串，结果，返回的最后一个长度会是 0`，然而，题目明确表示，`单词是指仅由字母组成、不包含任何空格字符的`，所以，在进行第 2 步之前，我们`要先对输入的字符串作处理，去掉两端的字符串（主要是去掉字符串最后的空格）`。然后在进行第 2 步操作。
4. 即可得到`正确答案`。


### Answer：

```js
// 错误答案
// 当 s = ‘a ’
var lengthOfLastWord = function(s) {
    let sArr = s.split(' ')
    return sArr[sArr.length - 1].length
};

// 正确答案
var lengthOfLastWord = function(s) {
    let sArr = s.trim().split(' ')
    return sArr[sArr.length - 1].length
};
```

### 其他：

本题更多 `JavaScript` 解析，点击链接访问对应的答案：[https://leetcode.com/problems/length-of-last-word/discuss?currentPage=1&orderBy=most_votes&query=javascript](https://leetcode.com/problems/length-of-last-word/discuss?currentPage=1&orderBy=most_votes&query=javascript)


