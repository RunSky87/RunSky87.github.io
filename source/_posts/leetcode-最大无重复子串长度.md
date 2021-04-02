---
title: leetcode-最大无重复子串长度
date: 2021-03-29 17:41:52
tags: leetcode
---

## 题目
给定一个字符串，请你找出其中不含有重复字符的 最长子串 的长度。
 
示例 1:
```
输入: s = "abcabcbb"
输出: 3 
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。

输入: s = "bbbbb"
输出: 1
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。

输入: s = "pwwkew"
输出: 3
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。
```
来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/longest-substring-without-repeating-characters

<!-- more -->

## 题解
方法：滑动窗口

我们使用两个指针表示字符串中的某个子串（或窗口）的左右边界,在每一步的操作中，我们会将左指针向右移动一格，表示我们开始枚举下一个字符作为起始位置，然后我们可以不断地向右移动右指针，但需要保证这两个指针对应的子串中没有重复的字符。
在移动结束后，这个子串就对应着 以左指针开始的，不包含重复字符的最长子串。我们记录下这个子串的长度；在枚举结束后，我们找到的最长的子串的长度即为答案。

```js
lengthOfLongestSubstring = function(s) {
  const n = s.length;
  if(n < 2) return n;
    
  let longestSubstring = s[0];

  // 设置左右指针
  let lk = 0,rk = 1;
  let longestLength = 0;

  for (let lk = 0; lk < n; ++lk) {
    // 没重复的
    while(rk < n && longestSubstring.indexOf(s[rk]) == -1){
      longestSubstring += s[rk];
      rk++;
    }
        
    longestLength = Math.max(longestLength, rk - lk);

    // 找到重复的存储字符串中的位置
    var index = s.indexOf(s[rk],lk);
        
    // 添加进来重复的这个值
    longestSubstring += s[rk];
    rk++;

    // 截取新的字符串
    if(index != -1) longestSubstring = s.substring(index + 1,rk);

    // 更新起始点
    if(index > lk) lk = index;

    // 满足退出条件
    if(rk >= n) return longestLength;
  }
  return longestLength;
};
```
