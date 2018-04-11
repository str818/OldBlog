---
layout: post
title: 【LeetCode】4_Median Of Two Sorted Arrays
categories: [LeetCode]
tags: LeetCode
---

# 问题描述

有两个有序数组num1与nums2，数组长度分别为m和n，找出两个有序数组的中位数，要求时间复杂度为O(log(m+n))。


### 输入

> nums1 = [1,3]
> nums2 = [2]

> nums1 = [1,2]
> nums2 = [3,4]

# 输出

> 2.0

> 2.5

# 我的解法

如果不要求时间复杂度的话肯定就是先排序再找中位数了，但是要求了时间复杂度为O(log(m+n))，那就只能使用二分法了，一个数组很容易二分，两个数组就需要
有一点难度了。

首先，如果两个数组的总长度是偶数，那中位数就是中间两个数的均值；如果两个数组的总长度是计数，中位数就是中间的数。那么，可以将
问题转化成；"如何找到两个数组中第k小的数"，有了第k小的数就能很容易的求中位数了。

可以使用递归的方法实现，getKth(A,m,B,n,k)。举个例子说明，A={1,3,5,7};B={2,4,6,8,10}，如果要求第7小的数，A中元素为4个，
B中的元素个数为6；k/2=7/2=3，而A中的第3个数A[2]=5;B中的第3个数B[2]=6;而A[2]<B[2];则A[0]、A[1]、A[2]中必然不可能有
第7小的数。因为A[2]<B[2]，所以比A[2]小的数最多可能是A[0]、A[1]、B[0]、B[1]这四个数，也就是说A[2]最多可能是第
5小的数，这样能够把A[0]、A[1]、A[2]抹去，变为getKth(A',m+3,B,0,7-3)，递归直到找到第k小的数。

```java
public static double findMedianSortedArrays(int[] nums1, int[] nums2) {
	int n = nums1.length +  nums2.length;
	if(n%2==0)
		return (getKth(nums1,0,nums2,0,n/2) + getKth(nums1,0,nums2,0,n/2+1))/2.0;
	else
		return getKth(nums1,0,nums2,0,n/2+1);
}
//找到第k小的数
public static int getKth(int[] A,int m,int[] B,int n,int k) {
	if(m>=A.length) return B[n+k-1];
	if(n>=B.length) return A[m+k-1];
	if(k==1) return Math.min(A[m], B[n]);
	
	int key1 = m+k/2-1>=A.length?Integer.MAX_VALUE:A[m+k/2-1];
	int key2 = n+k/2-1>=B.length?Integer.MAX_VALUE:B[n+k/2-1];
	if(key1<key2) { 
		return getKth(A,m+k/2,B,n,k-k/2);
	}else {
		return getKth(A,m,B,n+k/2,k-k/2);
	}
}
```