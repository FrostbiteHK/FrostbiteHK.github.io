---
layout:     post
title:      leetcode刷题
subtitle:   两数之和IV-输入BST
date:       2019-05-11
author:     HK
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - leetcode(simple)
---
# leetcode刷题记录
## 两数之和IV-输入BST

#### 题目描述：
给定一个二叉搜索树和一个目标结果，如果 BST 中存在两个元素且它们的和等于给定的目标结果，则返回 true。

案例 1:

    输入: 
        5
       / \
      3   6
     / \   \
    2   4   7

    Target = 9

    输出: True


案例 2:

    输入: 
        5
       / \
      3   6
     / \   \
    2   4   7

    Target = 28

    输出: False
    
#### 解题思路：BST的中序遍历 + 双指针
BST中序遍历得到节点的升序结果，然后再采用双指针法，一个指针指向最右边，一个指向最左边，然后进行遍历比较，如果差值大于最左边的值，则将右边指针左移（即小值增大），
如果小于最左边的值，则将左边指针右移（即大值变小），如果相等，则return true。
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    private ArrayList<Integer> list = new ArrayList<>();
    public boolean findTarget(TreeNode root, int k) {
        inOrder(root, list);
        int size = list.size();
        int left = 0, right = size - 1;
        while(left < right){
            int value = list.get(left) + list.get(right);
            if(value == k)
                return true;
            else if(value > k)
                right--;
            else
                left++;
        }
        return false;
    }
    
    public void inOrder(TreeNode root, ArrayList<Integer> list){
        if(root != null){
            inOrder(root.left, list);
            list.add(root.val);
            inOrder(root.right, list);
        }
    }
}
```
