## problem
Given a binary tree, return the inorder traversal of its nodes' values.

Example:

Input: [1,null,2,3]
   1
    \
     2
    /
   3

Output: [1,3,2]

Follow up: Recursive solution is trivial, could you do it iteratively?

## 代码实现
```C++
class Solution {
public:
   vector<int> inorderTraversal(TreeNode* root) {
        vector<int> res;
        if(root==NULL)
            return res;
        vector<int> left = inorderTraversal(root->left);
        vector<int> right = inorderTraversal(root->right);
        res.insert(res.end(), left.begin(), left.end());
        res.push_back(root->val);
        res.insert(res.end(),right.begin(),right.end());
        return res;
    }
};
```
