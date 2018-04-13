# path sum
二叉树问题
## problem
Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.

For example:
Given the below binary tree and sum = 22,

              5
             / \
            4   8
           /   / \
          11  13  4
         /  \      \
        7    2      1

return true, as there exist a root-to-leaf path 5->4->11->2 which sum is 22.
## 问题分析
题意是遍历树的顶部到底部，各元素的和相加，看是否有能与给定sum相等的数
## 代码实现
```C++
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

bool hasPathSum(TreeNode *root, int sum) {
        if (root == NULL) 
            return false;//若头指针即为空，没有元素可以相加，自然是false
        if (root->val == sum && root->left ==  NULL && root->right == NULL)//根部即与sum相等，且没有下一个指针，则为true 
            return true;
        return hasPathSum(root->left, sum-root->val) || hasPathSum(root->right, sum-root->val);//继续往下遍历，此时参数改为sum-root-val，看每一个节点左右子树是否能找到相等的和
 
    }
};
```


