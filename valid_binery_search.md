# Valid Binery Search
## description
 Given a binary tree, determine if it is a valid binary search tree (BST).

Assume a BST is defined as follows:

    The left subtree of a node contains only nodes with keys less than the node's key.
    The right subtree of a node contains only nodes with keys greater than the node's key.
    Both the left and right subtrees must also be binary search trees.

Example 1:

    2
   / \
  1   3

Binary tree [2,1,3], return true.

Example 2:

    1
   / \
  2   3

Binary tree [1,2,3], return false. 
## 问题分析
右子树的大小大于上一个节点，左子树的大小小于上一个节点，且每个节点都有左右子树，若是，返回true，否则，返回，false
## 编程实现
```C++
bool ValidTree(TreeNode *root)
{
  return isValidBST(root,NULL,NULL);
  }
bool isValidBST(TreeNode *root,TreeNode* minnode,TreeNode *maxnode)
{
  if(!root)return true;
  if(minnode&&minnode->val>root->val||maxnode&&maxnode->val<root->val)
    return false;
  return isValidBST(root->left,minnode,root)&&isValidBST(root->right,root,maxnode);
}
```
