我用JS刷LeetCode | Day 5 |  Valid Parentheses
### 有效的括号:

> 说明：现阶段的解题暂未考虑复杂度问题

首发地址：[http://www.brandhuang.com/article/1583660931568](http://www.brandhuang.com/article/1583660931568)

### Question：
Given a string containing just the characters `'(', ')', '{', '}', '[' and ']'`, determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.

Note that an empty string is also considered valid.

### 中文题目：

给定一个只包括` '('，')'，'{'，'}'，'['，']' `的字符串，判断字符串是否有效。

有效字符串需满足：

左括号必须用相同类型的右括号闭合。
左括号必须以正确的顺序闭合。

**注意:**

空字符串可被认为是有效字符串。

Example:

```javascript

Input: "()"
Output: true

Input: "()[]{}"
Output: true

Input: "(]"
Output: false

Input: "([)]"
Output: false

Input: "{[]}"
Output: true

```

### 个人分析：

1. 由题目「`空字符串可被认为是有效字符串`」, 当输入空字符串时，返回 `true`。
2. 声明一个对象`(Obj)`，用对象的 key 和 value 值来保存这成对出现的括号，要满足题目中`「有效的字符串」`,`必定是以左括号开始，右括号闭合`，所以我们用 `Obj` 的 `key` 来存左括号，`key` 对应的 `value` 值来存右括号。
3. 遍历输入的字符串，声明一个数组`(arr)`，来存放遍历出的和 `Obj` 中的 `key` 相等的字符。
4. 如果遍历出的元素`不是 Obj 中的 key`，说名此元素必定是一个`右括号`。
5. 取出第 3 步中存入数组中的字符，如果从数组中取出的值在`Obj` 中对应的 `value` 和第 4 步遍历出的元素`相同`，则说明是一个`有效的字符`，否则这个 `右括号` 没有对应的 `左括号`，是一个`无效的字符串`， 此时返回`false`。
6.  如果在遍历完输入的字符串后，第 3 步中的数组为空，则说明输入的字符串刚好都是 `有效的字符串`，否则是 `无效字符串`。
7. 得出如下答案。

### Answer：

```js
var isValid = function (s) {
    if (!s) return true
    let obj = {
        '(': ')',
        '{': '}',
        '[': ']',
    }
    let arr = []
    for (let i = 0; i < s.length; i++) {
        if (s[i] in obj) {
            arr.push(s[i])
        } else {
            var current = arr.pop()
            if (obj[current] !== s[i]) {
                return false
            }
        }
    }

    return arr.length === 0
};
```



### 其他：

本题更多 `JavaScript` 解析，点击链接访问对应的答案：[https://leetcode.com](https://leetcode.com/problems/valid-parentheses/discuss/?currentPage=1&orderBy=most_relevant&query=javascript)


