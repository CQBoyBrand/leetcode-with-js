我用JS刷LeetCode | Day 11 |  Plus One
###  加一:

> 说明：现阶段的解题暂未考虑复杂度问题

首发地址：[http://www.brandhuang.com/article/1584452962369](http://www.brandhuang.com/article/1584452962369)

### Question：
给定一个由整数组成的非空数组所表示的非负整数，在该数的基础上加一。

最高位数字存放在数组的首位， 数组中每个元素只存储单个数字。

你可以假设除了整数 0 之外，这个整数不会以零开头。

Example:

```javascript
输入: [1,2,3]
输出: [1,2,4]
解释: 输入数组表示数字 123。


输入: [4,3,2,1]
输出: [4,3,2,2]
解释: 输入数组表示数字 4321。
```

### 个人分析：
1. 分析题目：`数组非空非负且为整数`、`首位不为0`、`每个元素只存单个数字「即一位数」`。
2. 不知道有不小伙伴和我刚开始看到这题的想法一样？`将给定的数组转成字符串，然后转成数字进行加一，然后再加一后的数字转成字符串在转成数组，最后将数组中的元素转成数字`，代码见`错误答案`.
3. **`为什么第二步的答案错了呢？`** , 原因是：`javascript 只能进行正负2的53次方范围内的精确算数运算`，如果数组过长，就得不到我们想要的结果了，所以错误答案不是我们想要的。
4. 下面分析正确的答案：`要进行数字的加 1，肯定是从个位数开始加起「即给定数组的最后一位」`，所以我们从数组的最后一位开始遍历数组；
5. 由于题目告知 `每个元素只存单个数字`，所以当元素的值为 `9` 时，是一个特殊值，通过分析`特殊数组：[9]、[9,9]` ，可以得到，` [9] 进行加 1 应该变成 [1, 0]`，` [9， 9] 进行加 1 应该变成 [1, 0, 0]`;
6. 由上一步分析得：`遍历数组时，如果某元素值为 9，则将当前元素置为 0，否则就将该元素加一，并返回结果；如果遍历完数组还没有得到结果，说明元素的所有元素都是 9，所以原数组此时元素都已置为 0`，由第五步分析得：`需要在数组的最前面插入一个 1即可得到我们想要的结果`；这种方式还不是受到`第2、3步分析的限制`
7. 得到正确答案


### Answer：

```js
// 错误答案
var plusOne = function(digits) {
    let str = digits.join('') // 将数组元素拼接成字符串
    let newNum = Number(str) + 1 // 执行 加1的操作
    let newArr = newNum.toString().split('') // 将数字转成数组
    return newArr.map(Number) // 将数组中的字符串元素转成数字并返回结果
}

// 正确答案
var plusOne = function(digits) {
    for(let i = digits.length - 1; i>=0; i--){
        if(digits[i] === 9){
            digits[i] = 0
        } else{
            digits[i]++
            return digits
        }
    }
    digits.unshift(1)
    return digits
};
```

### 其他：

本题更多 `JavaScript` 解析，点击链接访问对应的答案：[https://leetcode.com](https://leetcode.com/problems/plus-one/discuss/?currentPage=1&orderBy=most_relevant&query=javascript)


