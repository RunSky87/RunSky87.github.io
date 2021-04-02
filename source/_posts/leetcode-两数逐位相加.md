---
title: leetcode-两数逐位相加
date: 2021-03-29 17:10:22
tags: leetcode
---

## 题目
给你两个非空的链表，表示两个非负的整数。它们每位数字都是按照 逆序 的方式存储的，并且每个节点只能存储一位数字。
请你将两个数相加，并以相同形式返回一个表示和的链表。

## 示例
```
输入：l1 = [2,4,3], l2 = [5,6,4]
输出：[7,0,8]
解释：342 + 465 = 807.

输入：l1 = [0], l2 = [0]
输出：[0]

输入：l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
输出：[8,9,9,9,0,0,0,1]
```
来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/add-two-numbers

<!-- more -->

## 题解
由于输入的两个链表都是逆序存储数字的位数的，因此两个链表中同一位置的数字可以直接相加。
我们同时遍历两个链表，逐位计算它们的和，并与当前位置的进位值相加。
具体而言，如果当前两个链表处相应位置的数字和为 n1+n2+carry 。
如果两个链表的长度不同，则可以认为长度短的链表的后面有若干个 00 。

```js
/**
 * 将两数组逐位相加
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 * @param {*} l1 
 * @param {*} l2 
 */
addTwoNumbers = function(l1, l2) {
  // head:结果，tail:中间值
  let head = null, tail = null;
  let carry = 0;

  while(l1 || l2){
    const n1 = l1 ? l1.val : 0;
    const n2 = l2 ? l2.val : 0;
    const sum = n1 + n2 + carry;
    const num = sum % 10;
    carry = Math.floor(sum / 10);
    
    if(!head){
      head = tail = new ListNode(num);
    }else{
      tail.next = new ListNode(num);
      tail = tail.next;
    }

    if(l1){
      l1 = l1.next;
    }
    if(l2){
      l2 = l2.next;
    }
  }

  if(carry > 0){
    tail.next = new ListNode(carry);
  }

  return head;
};
```
