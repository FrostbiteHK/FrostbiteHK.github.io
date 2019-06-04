---
layout:     post
title:      leetcode刷题
subtitle:   数组中的K-diff数对
date:       2019-04-29
author:     HK
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - leetcode(simple)-数组
---
# leetcode刷题记录
## 数组中的K-diff数对

#### 题目描述：
给定一个整数数组和一个整数 **k**, 你需要在数组里找到**不同**的 k-diff 数对。这里将 **k-diff** 数对定义为一个整数对 (i, j), 其中 i 和 j 都是数组中的数字，
且两数之差的绝对值是 k.

示例 1:

    输入: [3, 1, 4, 1, 5], k = 2
    输出: 2
    解释: 数组中有两个 2-diff 数对, (1, 3) 和 (3, 5)。
    尽管数组中有两个1，但我们只应返回不同的数对的数量。
示例 2:

    输入:[1, 2, 3, 4, 5], k = 1
    输出: 4
    解释: 数组中有四个 1-diff 数对, (1, 2), (2, 3), (3, 4) 和 (4, 5)。
示例 3:

    输入: [1, 3, 1, 5, 4], k = 0
    输出: 1
    解释: 数组中只有一个 0-diff 数对，(1, 1)。
注意:

* 数对 (i, j) 和数对 (j, i) 被算作同一数对。
* 数组的长度不超过10,000。
* 所有输入的整数的范围在 [-1e7, 1e7]。

#### 解题思路：使用HashMap存储，键为数组中元素，值为1或者map中键对应的值加1
```java
class Solution {
    public int findPairs(int[] nums, int k) {
        if(k < 0) return 0;
	int ans = 0;
	HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
	for(int num : nums){
	    map.put(num, map.containsKey(num)? 1+map.get(num):1);
	}
	if(k == 0){
	    for(int num : map.keySet()){
		if(map.get(num) > 1)
		    ans++;
	    }
	}else{
	    for(int num : map.keySet()){
		if(map.containsKey(num+k))
		    ans++;
		}
	    }
        return ans;
    }
}
```
