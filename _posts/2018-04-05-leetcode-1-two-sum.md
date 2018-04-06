---
layout: post
title: 【LeetCode】1_Two Sum
categories: [LeetCode]
tags: LeetCode
---

# 问题描述

有一个整型数组，返回数组中两个数的索引，使得这两个数相加得到一个指定的数（Target）

假定：每个输入的整型数组只有唯一解，并且数组中的每一个数不能重复使用

### 输入 
> nums = [2,7,11,15]　　　　target = 9

### 输出

> [0,1]

# 我的解法

不知道我当时再想什么，完全智障的想法，把问题想复杂了，也没有审题清楚，没有理解只是两个数相加。
```java
public static int[] twoSum(int[] nums, int target) {
    
	//初始Map
	HashMap<Integer,Integer> map = new HashMap<Integer,Integer>();	
	for(int i = 0;i<nums.length;i++) {
		map.put(i, nums[i]);
	}
		
	//Map降序排列
	ArrayList<Map.Entry<Integer, Integer>> list = 
		new ArrayList<Map.Entry<Integer, Integer>>(map.entrySet());  
	Collections.sort(list, new Comparator<Map.Entry<Integer, Integer>>() {  
		@Override
		public int compare(Map.Entry<Integer, Integer> arg0, Map.Entry<Integer, Integer> arg1) {
			return arg1.getValue().compareTo(arg0.getValue());
		}  
	}); 
	
	int[] result = new int[2];
	for(java.util.Map.Entry<Integer, Integer> entry_1: list){
		int key_1 = (int) entry_1.getKey();
		int val_1 = (int) entry_1.getValue();
		for(java.util.Map.Entry<Integer, Integer> entry_2: list) {
			int key_2 = (int) entry_2.getKey();
			int val_2 = (int) entry_2.getValue();
			if(key_1 != key_2 && val_1 + val_2 == target) {
				result[0] = key_1;
				result[1] = key_2;
				Arrays.sort(result);
				return result;
			}
		}
	}  
	return null;
}
```

# 解法一　暴力解法

最先想到的应该就是这种解法，时间复杂度$O(n^2)$，空间复杂度$O(1)$。

```java
public int[] twoSum(int[] nums, int target) {
	for (int i = 0; i < nums.length; i++) {
		for (int j = i + 1; j < nums.length; j++) {
			if (nums[j] == target - nums[i]) {
				return new int[] { i, j };
}}}}
```

# 解法二　HashMap（遍历两遍）

第一遍遍历是初始化HashMap，第二遍进行搜索。拿到一个数，用Target减去这个数，判断结果是否在HashMap中，再通过Map的Value找到Key。
时间复杂度$O(n)$，空间复杂度$O(n)$。

```java
public int[] twoSum(int[] nums, int target) {
	Map<Integer, Integer> map = new HashMap<>();
	for (int i = 0; i < nums.length; i++) {
		map.put(nums[i], i);
	}
	for (int i = 0; i < nums.length; i++) {
		int complement = target - nums[i];
		if (map.containsKey(complement) && map.get(complement) != i) {
			return new int[] { i, map.get(complement) };
		}
    }
	throw new IllegalArgumentException("No two sum solution");
}
```

# 解法三　HashMap（遍历一遍）

此方法很机智，边为Map赋值边搜索，将数组中的数值依次插入到Map中，该Map以数组中的值作为Key，以序号作为Value，
从数组中拿出一个元素值，到Map中寻找是否存在以（Target-元素值）为Value的键值对，若存在则表示该元素所对应的序号
与该键值对对应的值组成最终答案。

```java
public static int[] twoSum(int[] nums, int target) {
	Map<Integer, Integer> map = new HashMap<>();
	for (int i = 0; i < nums.length; i++) {
		int complement = target - nums[i];
		if (map.containsKey(complement)) {
			return new int[] { map.get(complement), i };
		}
		map.put(nums[i], i);
	}
	throw new IllegalArgumentException("No two sum solution");
}
```

