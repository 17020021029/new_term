# Minimum Path Sum
## problem 
Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right which minimizes the sum of all numbers along its path.

Note: You can only move either down or right at any point in time.

Example 1:

[[1,3,1],
 [1,5,1],
 [4,2,1]]

Given the above grid map, return 7. Because the path 1→3→1→1→1 minimizes the sum. 
## 问题分析
只能向下走和向右走，最后到达右下角，找到期间最小的元素和；遍历数组，不断更新res的值，res的每一个元素都代表遍历时列的值。最后一个元素就是最小值
## 编程实现
```C++
class Solution {
public:
    int minPathSum(vector<vector<int>>& grid) {
        if(grid.empty())
            return 0;
        vector<int> res(grid[0].size(),INT_MAX);
        res[0]=0;
        for(int i=0;i<grid.size();i++)
        {
            for(int j=0;j<grid[0].size();j++)
            {
                if(j>0)
                    res[j]=min(res[j],res[j-1])+grid[i][j];
                else 
                    res[j]=res[j]+grid[i][j];
            }
        }
        return res[grid[0].size()-1];
    }
};
```
