### 整数反转：
> 说明：现阶段的解题暂未考虑复杂度问题

首发地址：[http://www.brandhuang.com/article/1583415034915](http://www.brandhuang.com/article/1583415034915)

### Question：

Given a 32-bit signed integer, reverse digits of an integer.

Note:
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−231,  231 − 1]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

中文题目：

给出一个 32 位的有符号整数，你需要将这个整数中每位上的数字进行反转。

注意:

假设我们的环境只能存储得下 32 位的有符号整数，则其数值范围为[−2^31, 2^31− 1]。请根据这个假设，如果反转后整数溢出那么就返回 0。

Example:

```javascript
Input: 123
Output: 321

Input: -123
Output: -321

Input: 120
Output: 21

```

### 个人分析：

1. 关键点：「`整数`」、「`有符号`」、「`取值范围`」、「`反转后整数溢出返回 0`」。
2. 由于有取值范围，我们可以先求出上下限的值，可使用 `Math` 对象中的 `pow` 方法（`Math` 是 `JS` 内置对象，需要熟悉它）。
3. 看到题目中「`反转`」一词，应该很容易想到数组中有个 `reverse` 反转函数，然后，字符串的 `split` 方法可以将字符串转为数组，在转字符串时 `toString` 方法应该用的比较多。
4. 因为输入值可正可负，我们可以先求绝对值，使用 `Math.abs()`, 然后通过第 3 步取反。
5. 判断输入值的正负，决定输出值的符号。
6. 判断反转值和上下限的大小，如果超出范围直接返回 0。
7. 得出如下答案。

### Answer：

```js
var reverse = function(x) {
    var max = Math.pow(2, 31) - 1
    var min = Math.pow(-2, 31)
    var reverseX = Number(Math.abs(x).toString().split('').reverse().join(''))
    if (x > 0) {
        if (reverseX > max) {
            return 0
        } else {
            return reverseX
        }
    } else {
        if (-reverseX < min) {
            return 0
        } else {
            return -reverseX
        }
    }
};

```



### 其他：

本题更多 `JavaScript` 解析，点击链接访问对应的答案：[https://leetcode.com](https://leetcode.com/problems/reverse-integer/discuss/?currentPage=1&orderBy=most_relevant&query=javascript)


