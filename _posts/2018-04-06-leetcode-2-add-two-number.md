---
layout: post
title: 【LeetCode】2_Add Two Number
categories: [LeetCode]
tags: LeetCode
---

# 问题描述

用两个非空的链表表示两个非负数，两个非负数都是反序存储在链表中的，每个结点只包含一位数。
将两个非负数相加，并以链表的形式返回结果。

假定：两个数不会是以0开头，除了0本身

### 输入 
> (2 -> 4 -> 3) + (5 -> 6 -> 4)

### 输出

> 7 -> 0 -> 8

### 解释

> 342 + 465 = 807

# 我的解法

由于在每个链表中数值是翻转的，也就是说在链表的第一个结点是个位数，往后的结点依次类推：十位，百位...
那么可以很容易的想到用加法的规律，将两个链表从个位开始进行相加，依次向后进位。

关键的地方就是需要将所有的情况考虑周全，比如若列表一的长度比列表二长（l1=[0,1,2] l2=[0,1]），最后一位存在进位的情况（l1=[9,9] l2=[1]）。

```java

//结点类
//class ListNode{
//	int val;
//	ListNode next;
//	ListNode(int x){ val =x;}
//}

public static ListNode addTwoNumbers(ListNode l1, ListNode l2) {
	ListNode curr1 = l1;
	ListNode curr2 = l2;
	int next = 0;
		
	ListNode ans = null;
		
	ans = new ListNode(curr1.val + curr2.val);
	if(ans.val>9) {
		next = 1;
		ans.val %= 10;
	}
	curr1 = curr1.next;
	curr2 = curr2.next;
	ListNode curr = ans;
	while(curr1 != null || curr2 != null) {
			
		if(curr1 == null) {
			curr.next = new ListNode(curr2.val+next);
			curr = curr.next;
			curr2 = curr2.next;
			if(curr.val>9) {
				next = 1;
				curr.val %= 10;
			}else {
				next = 0;
			}
			continue;
		}
		if(curr2 == null) {
			curr.next = new ListNode(curr1.val+next);
			curr = curr.next;
			curr1 = curr1.next;
			if(curr.val>9) {
				next = 1;
				curr.val %= 10;
			}else {
				next = 0;
			}
			continue;
		}
			
		curr.next = new ListNode(curr1.val + curr2.val + next);
		curr = curr.next;
			
		if(curr.val>9) {
			next = 1;
			curr.val %= 10;
		}else {
			next = 0;
		}
			
		curr1 = curr1.next;
		curr2 = curr2.next;
	}
		
	if(next == 1) {
		curr.next = new ListNode(1);
	}
	return ans;
}
```

# 精简写法

这一思路与我的思路相同，但是写的十分精简，应该好好学习学习，时间复杂度O(max(m,n))，空间复杂度O(max(m,n))。

```java
public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
	ListNode dummyHead = new ListNode(0);
	ListNode p = l1, q = l2, curr = dummyHead;
	int carry = 0;
	while (p != null || q != null) {
		int x = (p != null) ? p.val : 0;
		int y = (q != null) ? q.val : 0;
		int sum = carry + x + y;
		carry = sum / 10;
		curr.next = new ListNode(sum % 10);
		curr = curr.next;
		if (p != null) p = p.next;
		if (q != null) q = q.next;
	}
	if (carry > 0) {
		curr.next = new ListNode(carry);
	}
	return dummyHead.next;//头结点是零结点，把第二个结点作为头结点返回
}
```
