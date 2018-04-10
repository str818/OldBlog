---
layout: post
title: 【LeetCode】6_ZigZag Conversion
categories: [LeetCode]
tags: LeetCode
---

# 问题描述

将一个字符串摆放成Z形状，比如字符串"PAYPALISHIRING"摆放成3行的Z形状为：
```
P   A   H   N
A P L S I I G
Y   I   R
```
按行可以读成字符串"PAHNAPLSIIGYIR"

本题需要将一个字符串摆放成n行的Z形状，并输出按行读的字符串。


# 我的解法

这是一道找规律的题目，先来分别看一下2、3与4行的形状，通过对比这些形状找出规律。
```
0     6
1   5 7         0   4   8        
2 4   8         1 3 5 7 9        0 2 4
3     9         2   6            1 3 5
```
以行数为4的形状为例，可以看出在行数为4的形状中，第1列与第4列的位置相差2×n-2(n=4)，我们知道第1列的字符序号为0到n-1，那么可以很容易的推断出第4列的字符序号，
但是第2列与第3列分别还有一个字符，需要找到一个规律计算出这两个字符的序号。仔细观察可以发现第3列元素的序号是7-2×1(行数)，而第
2列元素的需要为8-2×2(行数)。这样通过第一列的字符序号就能推断出对应行所有的元素序号。

```java
public static String convert(String s,int numRows) {
	if(numRows == 1 || s.length() < numRows) return s;
	StringBuilder ans = new StringBuilder();
	for(int i = 0; i < numRows; i++) {
		int index = i;
		while(index<s.length()) {
			ans.append(s.charAt(index));
			index += 2*numRows-2;
			//除了首尾两行其余的行均需要计算中间的序号
			if(i != 0 && i != numRows-1 && index - 2*i<s.length()) {
				ans.append(s.charAt(index - 2*i));
			}
		}
	}
	return ans.toString();
}
```