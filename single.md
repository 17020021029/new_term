# Single Number II
## Problem 
 Given an array of integers, every element appears three times except for one, which appears exactly once. Find that single one.

Note:
Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory? 
## 问题分析&&解题思路
用C++写，用是sort函数对数组进行排序的话相当容易，这样的话，在排序后的数组中，遍历，若元素与前后一个都不想等，则为返回元素</br>
*特别注意第一个和最后一个*
## 代码实现
```ruby
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        if(nums[0]!=nums[1])
            return nums[0];
        if(nums[nums.size()-1]!=nums[nums.size()-2])
            return nums[nums.size()-1];
        for(int i=0;i<nums.size()-1;i++)
        {
            if(nums[i]!=nums[i-1] && nums[i]!=nums[i+1])
                return nums[i];
        }
    }
};
```
## 总结
这道题用c++写起来比较容易，因为有sort函数,若是用C写，那必须也得自写一个快排函数以减少时间复杂度，这个不知道是不是满足时间复杂度，改天再试
