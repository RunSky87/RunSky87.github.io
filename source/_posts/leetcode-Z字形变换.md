---
title: leetcode-Z字形变换
date: 2021-04-02 20:18:38
tags: leetcode
---

## 题目
将一个给定字符串 `s` 根据给定的行数 `numRows` ，以从上往下、从左到右进行 `Z` 字形排列。

## 示例
```
输入：s = "PAYPALISHIRING", numRows = 4
输出："PINALSIGYAHRPI"
解释：
P     I    N
A   L S  I G
Y A   H R
P     I
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/zigzag-conversion

<!-- more -->

## 题解
### 按行数组拆分计算
```js
/**
 * @param {string} s
 * @param {number} numRows
 * @return {string}
 */
var convert = function(s, numRows) {
  if(numRows == 1 || numRows >= s.length) return s;

  let arr = new Array(numRows).fill('');
  let index = 0;
  let goingDown = true;
  for(let c of s){
      arr[index] += c;
      index += goingDown ? 1 : -1;
      if(index === numRows - 1) goingDown = false;
      if(index === 0) goingDown = true;
  }
  return arr.join('');
};
```

### 一个个计算
```js
/**
 * @param {string} s
 * @param {number} numRows
 * @return {string}
 */
var convert = function(s, numRows) {
  if(numRows == 1 || numRows >= s.length) return s;
  
  let ans = '';
  var space = 2 * numRows - 2;

  // 第 i 行
  for(let i = 0; i < numRows; i++){

      // 每行中的值，是跳过中间部分的值
      for(let j = 0; i+j < s.length;j+=space){
          if(i == 0) {
               ans += s[j];
          } else if(i == numRows - 1) {
              ans += s[j + numRows - 1]
          } else{
              if(s[j + i]) ans += s[j + i];
              if(s[j + space - i]) ans += s[j + space - i];
          }
      }
  }

  return ans;
};
```
