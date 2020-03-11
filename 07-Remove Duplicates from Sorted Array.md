我用JS刷LeetCode | Day 7 |  Remove Duplicates from Sorted Array
### 删除排序数组中的重复项:

> 说明：现阶段的解题暂未考虑复杂度问题

首发地址：[http://www.brandhuang.com/article/1583928356964](http://www.brandhuang.com/article/1583928356964)

### Question：
Given a sorted array nums, remove the duplicates in-place such that each element appear only once and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.


### 中文题目：

给定一个排序数组，你需要在 原地 删除重复出现的元素，使得每个元素只出现一次，返回移除后数组的新长度。

不要使用额外的数组空间，你必须在原地修改输入数组 并在使用 O(1) 额外空间的条件下完成。

Example:

```javascript

Given nums = [1,1,2],

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.

It doesn't matter what you leave beyond the returned length.


Given nums = [0,0,1,1,1,2,2,3,3,4],

Your function should return length = 5, with the first five elements of nums being modified to 0, 1, 2, 3, and 4 respectively.

It doesn't matter what values are set beyond the returned length.
```

### 个人分析：
1. 这道题就是我平时经常用到的数组去重，除了题目加了一个限制条件：`「不要使用额外的数组空间，你必须在原地修改输入数组」`。
2. 我给出的答案是一种在 `es5` 中比较常见的一种 `for循环` 方式（`答案一`），`比较相邻两元素是否相同，如果相同则从数组中删去第二个`。
3. 看了大神们的答案，题目中提到 `「你不需要考虑数组中超出新长度后面的元素。」`，所以有了 `答案二`, 直接从第 0 位开始替换原数组中的值。



### Answer：

```js
// 答案一
var removeDuplicates = function(arr) {
    for(var i=0; i<arr.length; i++){
            for(var j=i+1; j<arr.length; j++){
                if(arr[i] === arr[j]){         
                    arr.splice(j,1);
                    j--;
                }
            }
        }
    return arr.length
};
// 答案二
var removeDuplicates = function(arr) {
      var i = 0;
    arr.forEach(function (elem) {
        if (elem !== arr[i]) {
            arr[++i] = elem;
        }
    });
    return i + 1;
};
```



### 其他：

本题更多 `JavaScript` 解析，点击链接访问对应的答案：[https://leetcode.com](https://leetcode.com/problems/remove-duplicates-from-sorted-array/discuss/?currentPage=1&orderBy=most_relevant&query=javascript)


