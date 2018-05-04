# Combination
## problem
Given a set of candidate numbers (C) (without duplicates) and a target number (T), find all unique combinations in C where the candidate numbers sums to T.

The same repeated number may be chosen from C unlimited number of times.

Note:
All numbers (including target) will be positive integers.
The solution set must not contain duplicate combinations.
For example, given candidate set [2, 3, 6, 7] and target 7, 
A solution set is: 
[
  [7],
  [2, 2, 3]
]
## 问题分析
找到和为target值的vector，可以重复，数组从小到大排列，有多组
## 解题思路
写一个找到返回值的函数，其中参数target，每在数组加上一个元素，则减去这个元素的值，在从当前元素遍历，直到target值减为0
## 代码实现
```C++
class Solution {
public:
    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        sort(candidates.begin(),candidates.end());
        vector<vector<int>> res;
        vector<int> temp;
        get_vector(candidates,res,temp,target,0);
        return res;
    }
    void get_vector(vector<int>& candidates,vector<vector<int>>&res,vector<int> temp,int target,int idex)
    {
        if(target<0)return;
        if(target==0){
            res.push_back(temp);
            return;
        }
        for(int i=idex;i<candidates.size();i++)
        {
            temp.push_back(candidates[i]);
            get_vector(candidates,res,temp,target-candidates[i],i);
            temp.pop_back();
        }
    }
};
```
## 总结
[vector类用法](https://blog.csdn.net/hancunai0017/article/details/7032383)

## 二刷
学过STL后，按照这个思路写起来更得心应手了，但是用到递归，时间复杂度很大，所以还需要找更好的算法
