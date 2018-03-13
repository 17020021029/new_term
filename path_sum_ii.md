# Path Sum II
## Problem 
 Given a binary tree and a sum, find all root-to-leaf paths where each path's sum equals the given sum.
For example:
Given the below binary tree and sum = 22,
````
              5
             / \
            4   8
           /   / \
          11  13  4
         /  \    / \
        7    2  5   1
````
return
```
[
   [5,4,11,2],
   [5,8,4,5]
]
```
##  问题分析
求二叉树路径之和还要找出路径,需要用深度优先搜索DFS和二维的vector

## 代码实现
```C++
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {} //初始化列表
 * };
 */
class Solution {
public:
    vector<vector<int> > pathSum(TreeNode *root, int sum) {
        vector<vector<int>> res;
        vector<int> out;
        helper(root,sum,out,res);   //调用函数
        return res;
    }
    void helper(TreeNode* node,int sum,vector<int>& out,vector<vector<int>>& res)   //引用型
    {
        if(!node) return;   
        out.push_back(node->val);   //在out尾端加上结构体指针指向的数据
        if(sum==node->val && !node->left && !node->right)
        {
            res.push_back(out);
        }
        helper(node->left,sum-node->val,out,res);//递归调用，往下遍历二叉树
        helper(node->right,sum-node->val,out,res);
        out.pop_back(); //删掉out最后一个元素
    }
};
```
## 总结
这几天看了类和对象后终于理解了点c++代码，但是vector类的用法和注意事项等还没有学会，因此暂时处于看代码阶段
