---
layout:     post
title:      leetcode刷题
subtitle:   Excel表列序号
date:       2019-03-20
author:     HK
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - leetcode(simple)
---
# leetcode刷题记录
## Excel表列序号

#### 题目描述：
给定一个Excel表格中的列名称，返回其相应的列序号。

例如，

    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
    ...
*示例 1:*

    输入: "A"
    输出: 1

*示例 2:*

    输入: "AB"
    输出: 28

*示例 3:*

    输入: "ZY"
    输出: 701
    
#### 解题思路：26进制转10进制
```java
class Solution {
    public int titleToNumber(String s) {
        int res = 0, tmp, n = s.length();
        for(int i = 0; i < n; i++){
            tmp = s.charAt(i) - 'A' + 1;
            res = res*26 + tmp;
        }
        return res;
    }
}
```
