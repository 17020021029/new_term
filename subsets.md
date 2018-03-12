# Subsets
## Problem 
 Given a set of distinct integers, nums, return all possible subsets (the power set).

Note: The solution set must not contain duplicate subsets.

For example,
If nums = [1,2,3], a solution is:
````
[
  [3],
  [1],
  [2],
  [1,2,3],
  [1,3],
  [2,3],
  [1,2],
  []
]

````
## 问题分析
求集合中所有子集问题</br>
要求子集中元素非递减序排列,所以需要将原数组排序,所以构造子集方法可以构造一个二叉树或从第二层开始迭代
## 代码实现
```C++
class Solution {
public:
    vector<vector<int>> subsets(vector<int>& nums) {
        vector<vector<int>> result(1);
        sort(nums.begin(),nums.end());
        int i=0,j=0;
        for(i=0;i<nums.size();i++)
        {
            int  resultsize=result.size();
            for(j=0;j<resultsize;j++)
            {
                result.push_back(result[j]);
                result.back().push_back(nums[i]);
            }
        }
        return result;
    }
};
```
