我用JS刷LeetCode | Day 3 | Roman to Integer

### 罗马数字转整数：

> 说明：现阶段的解题暂未考虑复杂度问题

首发地址：[http://www.brandhuang.com/article/1583505287028](http://www.brandhuang.com/article/1583505287028)

### Question：

Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.

```md
Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
```
For example, two is written as II in Roman numeral, just two one's added together. Twelve is written as, XII, which is simply X + II. The number twenty seven is written as XXVII, which is XX + V + II.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. Instead, the number four is written as IV. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as IX. There are six instances where subtraction is used:

- I can be placed before V (5) and X (10) to make 4 and 9. 
- X can be placed before L (50) and C (100) to make 40 and 90. 
- C can be placed before D (500) and M (1000) to make 400 and 900.

Given a roman numeral, convert it to an integer. Input is guaranteed to be within the range from 1 to 3999.

中文题目：

罗马数字包含以下七种字符: I， V， X， L，C，D 和 M。
```md
字符          数值
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
```
例如， 罗马数字 2 写做 II ，即为两个并列的 1。12 写做 XII ，即为 X + II 。 27 写做  XXVII, 即为 XX + V + II 。

通常情况下，罗马数字中小的数字在大的数字的右边。但也存在特例，例如 4 不写做 IIII，而是 IV。数字 1 在数字 5 的左边，所表示的数等于大数 5 减小数 1 得到的数值 4 。同样地，数字 9 表示为 IX。这个特殊的规则只适用于以下六种情况：

- I 可以放在 V (5) 和 X (10) 的左边，来表示 4 和 9。
- X 可以放在 L (50) 和 C (100) 的左边，来表示 40 和 90。 
- C 可以放在 D (500) 和 M (1000) 的左边，来表示 400 和 900。

给定一个罗马数字，将其转换成整数。输入确保在 1 到 3999 的范围内。

Example:

```javascript
Input: "III"
Output: 3

Input: "IV"
Output: 4

Input: "IX"
Output: 9

Input: "LVIII"
Output: 58
Explanation: L = 50, V= 5, III = 3

Input: "MCMXCIV"
Output: 1994
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4

```

### 个人分析：

1. 罗马字符包含 `7` 种字符，可声明一个对象，对象的健和值分别用罗马字符及其对应的整数来表示。
2. 由题目中，罗马数字的特殊规则，可以看出一个规律：`小数放在大数左边并表示一个数时，大数与小数的比值为 5 或者 10，同时他们所表示的值为 大数减小数的差`.
3. 遍历输入的字符串，求出当前数字和和后一个数字的比值，由第 `2` 步，如果这两个数的比值为 `5` 或者 `10`。说明这两个字符组合表示为一个数，循环向后移一位（因为这一次循环用掉了两个位置）。
4. 如果两个数的比值不是 `5` 或者 `10`，则直接在结果中加上当前的值。
5. 得出如下答案。

### Answer：

```js
var romanToInt = function(s) {
    let code = {
        'I': 1,
        'V': 5,
        'X': 10,
        'L': 50,
        'C': 100,
        'D': 500,
        'M': 1000,
    }
    let result = 0
    for (let i = 0; i < s.length; i++) {
        const current = code[s[i]];
        const next = code[s[i + 1]];

        if (next && ((next / current) == 5 || (next / current) == 10) ) {
            result += next - current
            i++
        } else {
            result +=  current
        }
        
    }
    return result
};

```



### 其他：

本题更多 `JavaScript` 解析，点击链接访问对应的答案：[https://leetcode.com](https://leetcode.com/problems/roman-to-integer/discuss/?currentPage=1&orderBy=most_relevant&query=javascript)


