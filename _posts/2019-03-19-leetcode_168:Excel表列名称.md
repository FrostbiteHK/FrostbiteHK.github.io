---
layout:     post
title:      leetcode刷题
subtitle:   Excel表列名称
date:       2019-03-19
author:     HK
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - leetcode(simple)
---
# leetcode刷题记录
## Excel表列名称

#### 题目描述：
给定一个正整数，返回它在 Excel 表中相对应的列名称。

例如，

      1 -> A
      2 -> B
      3 -> C
      ...
      26 -> Z
      27 -> AA
      28 -> AB 
      ...
示例 1:

    输入: 1
    输出: "A"
示例 2:

    输入: 28
    输出: "AB"
示例 3:

    输入: 701
    输出: "ZY"
    
#### 解题思路：
大神的一个解法~
```java
class Solution {
    public String convertToTitle(int n) {
        return n == 0 ? "" : convertToTitle(--n / 26) + (char)('A' + (n % 26));
    }
}
```
