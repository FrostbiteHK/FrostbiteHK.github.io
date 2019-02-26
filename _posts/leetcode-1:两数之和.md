---
layout:     post
title:      leetcode刷题
subtitle:   两数之和
date:       2019-02-25
author:     HK
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - leetcode
---
>leetcode刷题记录

## 两数之和
    给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那两个整数，并返回他们的数组下标。你可以假设每种输入只会对应一个答案。
    但是，你不能重复利用这个数组中同样的元素。
    示例:给定 nums = [2, 7, 11, 15], target = 9 ， 因为 nums[0] + nums[1] = 2 + 7 = 9 ，所以返回 [0, 1]
    
解题思路1：循环遍历两次数组，复杂度为O(n^2)

