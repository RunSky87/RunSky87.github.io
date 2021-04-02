---
title: leetcode-两数之和
date: 2021-03-29 15:08:44
tags: leetcode
---

## 题目
给定一个整数数组 `nums` 和一个整数目标值 `target`，请你在该数组中找出和为目标值 的那两个整数，并返回它们的数组下标。

你可以按任意顺序返回答案。

示例：
```
输入：nums = [2,7,11,15], target = 9
输出：[0,1]
解释：因为 nums[0] + nums[1] == 9 ，返回 [0, 1] 。
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/two-sum

<!-- more -->

## 题解
### 暴力枚举
```js
/**
 * @param {number[]} nums
 * @param {number} target
 */
var twoSum = function(nums, target) {
  for(let i = 0; i < nums.length; i++){
    for(let j = i + 1; j < nums.length; j++){
      if(nums[i] + nums[j] == target){
        return [i,j]
      }
    }
  }
}
```

### 哈希表
我们创建一个哈希表，对于每一个 `x`，我们首先查询哈希表中是否存在 `target - x`，然后将 `x` 插入到哈希表中，即可保证不会让 `x` 和自己匹配。

```js
var twoSum = function(nums, target) {
  var hashtable = [];
  for(let i = 0; i < nums.length; i++){
    if(typeof hashtable[target - nums[i]] == "number"){
      return [i,hashtable[target - nums[i]]]
    }
    hashtable[nums[i]] = i;
  }
}
```
