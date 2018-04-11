---
layout: post
title: 【LeetCode】7_Reverse Integer
categories: [LeetCode]
tags: LeetCode
---

# 问题描述

将一个32bit的带符号整数反转，假定如果超出32bit则返回0

### 输入

> 123

> -123

> 120

# 输出

> 321

> -321

> 21

# 我的解法

将该整数转化成一个字符串，用StringBulider的内置方法反转字符串，强制转化为整型，由于整型是32bit，用异常处理机制判断是否溢出。

```java
public static int reverse(int x) {
	StringBuilder s = new StringBuilder(x+"");			
	if(s.charAt(0)!='-') s.insert(0, '+');		
	String ans= new StringBuilder(s.substring(1, s.length())).reverse().toString();
	try{
		return Integer.parseInt(s.charAt(0)+ans);
	}catch (NumberFormatException e){
		return 0;
	}
}
```

# 解法一

基本操作

```java
public static int reverse(int x) {
	int ans = 0,newAns = 0;
	while(x!=0) {
		newAns = ans*10 + x%10;
		if(ans != (newAns - x%10)/10) return 0;//判断是否溢出
		ans = newAns;
		x/=10;
	}
	return ans;	
}
```

# 解法二

用空间更大的long存储整数

```java
public static int reverse(int x) {
	long ans = 0;
	while(x!=0) {
		ans = ans*10+x%10;
		x/=10;
	}
	//if(ans < Integer.MIN_VALUE || ans > Integer.MAX_VALUE)
	//	return 0;
	//return (int)ans;
	int test = (int) ans;
    return ans == test ? test : 0;
}
```