---
layout: post
title: 【LeetCode】3_Longest Substring Without Repeating Characters
categories: [LeetCode]
tags: LeetCode
---

# 问题描述

给定一个字符串，返回最长无重复的子字符串的长度

### 输入 
> abcabcbb

> bbbbb

> pwwkew

### 输出

> 3

> 1

> 3

### 解释

> abc

> b

> wke

# 我的解法

暴力求解，虽然能出来正确结果，但时间复杂度太高$O(n^3)$，不能通过。
依次以每个字符开头向后寻找最长的子字符串，通过比较得出最大的子字符串

```java
public static int lengthOfLongestSubstring(String s) {
		
	int maxLength = 0;
	String subString = null;
	if(s.length() == 1) maxLength = 1;//考虑长度为1的字符串
		
	for(int i = 0; i < s.length(); i++) {
		subString = s.charAt(i)+"";
		for(int j = i+1; j< s.length();j++) {
			if(subString.indexOf(s.charAt(j))>=0) break;
			subString += s.charAt(j);
		}
		if(subString.length()>maxLength) maxLength = subString.length();
	}
	return maxLength;
}
```

# 滑动窗口法

比如abcabc，当右边扫描到abca时把第一个a删除得道bca，然后“窗口”继续向右滑动，每当添加一个新的字符时，
检查“窗口”中有没有重复的字符，如果没有重复就添加进“窗口”，有重复的话就扔掉“窗口”左面重复的部分，经过这一过程从而得道最大窗口。
时间复杂度为O(n)。
```java
public int lengthOfLongestSubstring(String s) {
	int n = s.length();
	Set<Character> set = new HashSet<>();
	int ans = 0, i = 0, j = 0;
	while (i < n && j < n) {
		// try to extend the range [i, j]
		if (!set.contains(s.charAt(j))){
			set.add(s.charAt(j++));
			ans = Math.max(ans, j - i);
		}
		else {
			set.remove(s.charAt(i++));
		}
	}
	return ans;
}
```
