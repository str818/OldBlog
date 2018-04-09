---
layout: post
title: 【LeetCode】5_Longest Palindromic Substring
categories: [LeetCode]
tags: LeetCode
---

# 问题描述

给出字符串s，找出s中最长回文子字符串，假定字符串s的最大长度为1000。

### 输入 
> babad

> cbbd

### 输出

> bab(aba)

> bb

# 我的解法

首先想到的肯定是暴力求解喔，判断每一个子字符串是不是回文字符串，但是这样做时间复杂度高达$O(n^3)$，肯定是不能Accepted的。

我的思路是，既然是找最长的，那就从最长的子字符串开始判断，一直找到最短的子字符串，在这过程中只要找到了一个回文字符串，那么这一字符串就是最长的回文字符串。

```java
public static String longestPalindrome(String s) { 
	int n = s.length();
	//长度为i的回文数
	for (int i = n; i>0; i--) {
		for(int j = 0; j<=n-i; j++) {
			if(isPalindromic(s.substring(j, j+i))) 
				return s.substring(j, j+i);
		}
	}
	return null;
}
//判断是否为回文字符串                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
public static boolean isPalindromic(String s) {
	int n = s.length();
	for(int i=0; i<=n/2; i++) {
		if(s.charAt(i) != s.charAt(n-i-1)) return false; 
	}
	return true;	
}
```

# 中心扩展法

遍历字符串的每一个字符，如果存在回文子串，那么中心是某一字符(奇数)或两个字符的空隙(偶数)，然后分两种情况向两边扩展。

```java
private static int low;//回文子串的起始位置
private static int maxLen;//回文子串的最大长度
public String longestPalindrome(String s) {
	int len=s.length();
	if(len<2) return s;
	for(int i=0;i<len;i++){
		extendPalindrome(s,i,i);//回文子串是奇数的情况
		extendPalindrome(s,i,i+1);//回文子串是偶数的情况
	}
	return s.substring(low, low+maxLen);
}
private static void extendPalindrome(String s, int j, int k) {
	while(j>=0&&k<s.length()&&s.charAt(j)==s.charAt(k)){
		j--;
		k++;
	}
	if(maxLen<k-j-1){
		low=j+1;
		maxLen=k-j-1;
	}    
}
```

