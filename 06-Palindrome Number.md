我用JS刷LeetCode | Day 6 |  Palindrome Number
### 回文数:

> 说明：现阶段的解题暂未考虑复杂度问题

首发地址：[http://www.brandhuang.com/article/1583842055249](http://www.brandhuang.com/article/1583842055249)

### Question：
Determine whether an integer is a palindrome. An integer is a palindrome when it reads the same backward as forward.

Coud you solve it without converting the integer to a string?

### 中文题目：

判断一个整数是否是回文数。回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。

**注意:**

你能不将整数转为字符串来解决这个问题吗？

Example:

```javascript

Input: 121
Output: true

Input: -121
Output: false

Input: 10
Output: false

```

### 个人分析：

1. 看到题目`「回文数字」`，我们第一反应很有可能就是将数字先转成字符串然后转成数组，最后利用数组的 `reverse` 方法进行倒序，然后转换成数字来判断原数字新数字是否相等即可，即 `答案一`。
2. 我们可以分析下`回文数`的特点可以发现，他是一个`对称结构的数`,所以从两端向中间遍历，如果遍历出的两个字符不相等，则说明不是`回文数`，直接返回 `false`，，否则一直遍历到从两端遍历的交叉点为止。所以有了`答案二`。
3. `但是`，题目最后还有个问题：`「你能不将整数转为字符串来解决这个问题吗？」`。
4. 不转成字符串的方法我`没有做出来！`，看了大神们的答案后简单分析下 `答案三`。
5. 主要思路就是`把数字翻过了，然后和输入值进行比较`，如果相等，则是回文数，否则不是回文数。
6. 声明一个 `s`变量来存输入的 `x`，声明一个 `rev`变量来存输入的数字的个位数。
7. 当把输入值的个位数移到变量 `rev` 中后，输入值的位数少了一位，所以有新的 `s` 值变成了 `s / 10`。`Math.floor(s / 10)` 是取整方便计算。
8. `rev` 的值每次循环都会增加一位，所以新的 `rev` 变成了 `上一步中的 rev 乘以 10`然后加上这一步中的 `s的个位数`。
9. 直到 `s` 变为 0 时循环停止，此时`比较原输入值和倒序后的值，若相等，则是回文数,否则不是回文数`。
10. 得出`答案三`。

### Answer：

#### 一、答案一
```js
var isPalindrome = function(x) {
    return x === Number(x.toString().split('').reverse().join(''))
};
```


#### 二、答案二
```js
var isPalindrome = function(x) {
    let xStr = x.toString()
    let i = 0; // 头部
    let j = xStr.length - 1 // 尾部
    while(i < j){
         if(xStr[i] !== xStr[j]) {
             return false;
         } else{
            i ++;
            j --;
        }
    }
    return true
};
```
#### 三、答案三
```js
var isPalindrome = function(x) {
    let s = x;
    let rev = 0
    while (s > 0) {
        rev = rev * 10 + s % 10
        s = Math.floor(s / 10)
    }
    return x === rev
};
```



### 其他：

本题更多 `JavaScript` 解析，点击链接访问对应的答案：[https://leetcode.com](https://leetcode.com/problems/palindrome-number/discuss/?currentPage=1&orderBy=most_relevant&query=JavaScript)


