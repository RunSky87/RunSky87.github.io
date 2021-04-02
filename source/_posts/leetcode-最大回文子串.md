---
title: leetcode-最大回文子串
date: 2021-03-30 16:49:14
tags: leetcode
---

## 题目
求字符串的最长回文子串

## 示例
```
输入: "babad"
输出: "bab"
注意: "aba" 也是一个有效答案
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/longest-palindromic-substring
<!-- more -->

## 题解
### 暴力解法
```js
/**
 * @param {string} s
 * @return {string}
 */
var longestPalindrome = function(s) {
  let len = s.length;
  if(len < 2) return s;
  
  // 最大长度
  let maxLen = 1;
  
  // 获取第一个值
  let res = s.substring(0,1);
  
  // 枚举所有长度大于等于 2 的子串
  for(let i = 0; i < len - 1; i++){
    for(let j = i + 1; j < len; j++){
      
      // 如果是回文串
      if(valid(s,i,j)){
        
        // 如果回文串长度大于已存储长度
        if((j + 1) - i > maxLen)
        {
          res = s.substring(i,j+1);
          maxLen = res.length;
        }
      }
    }
  }

  return res;
};
  

// 计算字符串节点内是不是回文串
let valid = function(s,left,right){
  
  // 验证子串 s[left,right] 是不是回文串
  while(left < right){
    if(s.charAt(left) != s.charAt(right))
    {
      return false;
    }
    left++;
    right--;
  }
  
  return true;
}
```

### 动态规划
从回文串的定义展开讨论：
- 如果一个字符串的头尾两个字符都不相等，那么这个字符串一定不是回文串；
- 如果一个字符串的头尾两个字符相等，才有必要继续判断下去。
- 如果里面的子串是回文，整体就是回文串；
- 如果里面的子串不是回文串，整体就不是回文串。

```js
var longestPalindrome = function(s) {
  let len = s.length;
  let ans = "";
  
  // 初始化一个二维矩阵
  var arr = new Array(len).fill().map(() => new Array(len).fill(false));

  // 字符串长度
  for(let del = 0; del < len; del++){
    
    // 字符串起点位置
    for(let i = 0; i < len - del; i++){
      
      // 字符串终点位置
      let j = i + del;
 
      // 如果只有一个字符，属于回文
      if(del == 0){ arr[i][j] = true}

      // 如果只有两个字符，则它们相等为回文
      else if(del == 1) { arr[i][j] = s.charAt(i) == s.charAt(j)}
      
      // 如果有多个字符，则它们相等 并且 它们里面的两个相等，为回文
      // 它们内部的字符为 起点后一位到终点前一位 [i+1][j-1]
      // 计算过程是根据子串长度从小到大计算的，它们在之前被计算过
      else { arr[i][j] = s.charAt(i) == s.charAt(j) && arr[i+1][j-1] }
      
      // 如果当前子串是回文字符串
      if(arr[i][j] && del >= ans.length){
        ans = s.substring(i,j + 1)
      }
    }
  }
  return ans;
}
```

### 中心扩散
中心扩散法的思路是：遍历每一个索引，以这个索引为中心，利用“回文串”中心对称的特点，往两边扩散，看最多能扩散多远。
我们可以设计一个方法，兼容以上两种情况：
1、如果传入重合的索引编码，进行中心扩散，此时得到的回文子串的长度是奇数；
2、如果传入相邻的索引编码，进行中心扩散，此时得到的回文子串的长度是偶数。

```js
const longestPalindrome = function(s) {
  let len = s.length;
  if(len < 2) return s;
  
  let start = 0, end = 0;
  for(let i = 0; i < len; i++){
    // 一个字符为中心的回文子串
    let len1 = expandAroundCenter(s,i,i);
    
    // 两个相同字符为中心的回文子串
    let len2 = expandAroundCenter(s,i,i+1);
    
    let longest = Math.max(len1,len2);
    
    // 如果当前回文字符串长度为史上最长，则更新最大回文字符串两端位置
    if(longest > end - start){
      
      // 简化思路
      // let isOdd = longest % 2 == 1;
      
      // start = i - (isOdd ? (longest - 1) / 2 : (longest - 2) / 2);
      start = i - Math.floor((longest - 1) / 2);
      
      // end = i + (isOdd ? (longest - 1) / 2 : longest / 2)
      end = i + Math.floor(longest / 2);
    }
  }
  
  return s.substring(start,end+1)
}

// 向两边扩散 判断是否是回文字符串
const expandAroundCenter = function(s,left,right){
  while(left >= 0 &&
        right <= s.length &&
        s.charAt(left) == s.charAt(right)){
    left--;
    right++;
  }
  
  // 当跳出 while 循环时，s.charAt(left) != s.charAt(right)
  // 所以回文字符串长度为 (right - 1 + 1) - (left + 1),如下 
  return --right + 1 - ++left;
}
```
