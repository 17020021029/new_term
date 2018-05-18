## Problem
Given a binary tree, return the preorder traversal of its nodes' values.

Example:

Input: [1,null,2,3]
   1
    \
     2
    /
   3

Output: [1,2,3]
Follow up: Recursive solution is trivial, could you do it iteratively?
## 解题思路
正序遍历二叉树，放入vector中，很easy的一道题，但是要注意是从左到右
## 代码实现
 ``` C++
 /**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<int> preorderTraversal(TreeNode* root) {
        vector<int> res;
        getVector(root,res);
        return res;
    }
    void getVector(TreeNode* root,vector<int>& res){
        if(root==NULL)
            return;
        res.push_back(root->val);
        getVector(root->left,res);
        getVector(root->right,res);
    }
};
 ```
