#  Unique Binary Search Trees
## problem
Given n, how many structurally unique BST's (binary search trees) that store values 1...n?

For example,
Given n = 3, there are a total of 5 unique BST's. 
````
  1         3     3      2      1
    \       /     /      / \      \
     3     2     1      1   3      2
    /     /       \                 \
   2     1         2                 3
````
## 问题分析
一开始看了很长时间没看出来该怎么做，后来看到有人的解法说这个是卡特兰数列的一个例子

![卡特兰数](https://gss2.bdstatic.com/9fo3dSag_xI4khGkpoWK1HF6hhy/baike/s%3D256/sign=2300064332dbb6fd215be2233f25aba6/1f178a82b9014a9084d9f405a2773912b21beea7.jpg)
## 代码实现
```C++
class Solution {
public:
    int numTrees(int n) {
        vector<int> dp(n+1,0);
        dp[0]=1;
        dp[1]=1;
        for(int i=2;i<=n;i++)
        {
            for(int j=0;j<i;j++)
            {
                dp[i]+=dp[j]*dp[i-j-1];
            }
        }
        return dp[n];
    }
};
```
