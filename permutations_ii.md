# Permutation II
## problem
 Given a collection of numbers that might contain duplicates, return all possible unique permutations.

For example,
[1,1,2] have the following unique permutations:

[
  [1,1,2],
  [1,2,1],
  [2,1,1]
]
## 问题分析&解题思路
给定一个数组，得到重新排列的所有数组的集合。看给定的一组数据，应该是按顺序排的，就要先对数组进行排序。重新组合的话最直接可以想到递归，每次进行组合，返回数组后，在进行，知道全部拍完
## 编程实现
```C++
class Solution {
public:
    vector<vector<int>> permuteUnique(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        vector<vector<int>> res;
        getres(res,0,nums.size(),nums);
        return res;
    }
    void getres(vector<vector<int>>&res,int i,int j,vector<int> nums)
    {
        if(i==j-1)
        {
            res.push_back(nums);
            return;
        }
        for(int k=i;k<j;k++)
        {
            if(nums[i]==nums[k]&&i!=k)
                continue;
            else{
                swap(nums[i],nums[k]);
                getres(res,i+1,j,nums);
            }
        }
    }
};
```
## 总结
第一次写的时候，nums用了引用，输出的结果多了数据，没太明白到底咋回事，说明引用还是掌握的不好
