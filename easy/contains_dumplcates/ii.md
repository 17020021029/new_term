## Problem 
Given an array of integers and an integer k, find out whether there are two distinct indices i and j in the array such that nums[i] = nums[j] and the absolute difference between i and j is at most k.

Example 1:

Input: [1,2,3,1], k = 3
Output: true

Example 2:

Input: [1,0,1,1], k = 1
Output: true

Example 3:

Input: [1,2,1], k = 0
Output: false


## 代码实现
```C++
class Solution {
public:
    bool containsNearbyDuplicate(vector<int>& nums, int k) {
        unordered_map<int,int> m;
        for(int i=0;i<nums.size();i++){
            if(m.find(nums[i])!=m.end()&&(i-m.find(nums[i])->second<=k))
                return true;
            m[nums[i]]=i;
        }
        return false;
    }
};
```
## 总结
unordered_map 的用法
