# Sum Root to left numbers
## problem
Given a binary tree containing digits from 0-9 only, each root-to-leaf path could represent a number.

An example is the root-to-leaf path 1->2->3 which represents the number 123.

Find the total sum of all root-to-leaf numbers.

For example,
```
    1
   / \
  2   3
```
The root-to-leaf path 1->2 represents the number 12.
The root-to-leaf path 1->3 represents the number 13.

Return the sum = 12 + 13 = 25. 
## 问题分析
写一个函数，遍历左右数，一直相加得到sum
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
    int sumNumbers(TreeNode* root) {
        if(!root)
            return 0;
        sum=0;
        DS(root,0);
        return sum;
    }
    void DFS(TreeNode *&temp,int currentSum)
    {
        currentSum=currentSum*10+temp->val;
        if(!temp->left&&!temp->right)
            sum+=currentSum;
        if(temp->left)
            DS(temp->left,currentSum);
        if(temp->right)
            DS(temp->right,currentSum);
    }
private:
    int sum;
};
```
## 总结体会
用到递归的思想，emmmm，还是很简单的
