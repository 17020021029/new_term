## problem
Given an array nums containing n + 1 integers where each integer is between 1 and n (inclusive), prove that at least one duplicate number must exist. Assume that there is only one duplicate number, find the duplicate one.

Example 1:

Input: [1,3,4,2,2]
Output: 2
Example 2:

Input: [3,1,3,4,2]
Output: 3
Note:

You must not modify the array (assume the array is read only).
You must use only constant, O(1) extra space.
Your runtime complexity should be less than O(n2).
There is only one duplicate number in the array, but it could be repeated more than once.
## 解题思路
题目提示依静很清楚了，几乎可以确定解题方法，提示说不用改变数组，若改变数字，可以一次遍历直接判断，规定时间复杂度为O(n^2),直接两次遍历就能过
## 代码实现
```C++
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        for(int i=0;i<nums.size();i++){
            for(int j=i+1;j<nums.size();j++){
                if(nums[j]==nums[i])
                    return nums[i];
            }
        }
    }
};
```
