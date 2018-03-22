# FInd Minimum in Rotated Array
## Problem 
Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

(i.e., 0 1 2 4 5 6 7 might become 4 5 6 7 0 1 2).

Find the minimum element.

You may assume no duplicate exists in the array.
## 问题分析
这道题目和之前做过的找目标值的那题题意类似，于是想都没想就直接套用代码，结果rte
## 编程实现
run time error
```
class Solution {
public:
    int findMin(vector<int>& nums) {
        int begin=0;
        int end=nums.size()-1;
        int mid;
        while(begin<=end)
        {
            mid=(begin+end)/2;
            if(nums[mid-1]>=nums[mid]&&nums[mid+1]>=nums[mid])
                return nums[mid];
            else if(nums[mid]>=nums[begin])//左边是有序的
            {
                begin=mid+1;
            }
            else if(nums[mid]<=nums[end])//右边是有序的
            {
                end=mid-1;
            }
        }
        
    }
};
```
AC
```c++
class Solution {
public:
    int findMin(vector<int>& nums) {
        int begin=0;
        int end=nums.size()-1;
        while(begin<end)
        {
            if(nums[begin]<nums[end])
                return nums[begin];
            int mid=(begin+end)/2;
            if(nums[mid]>nums[end])
            {
                begin=mid+1;
            }
            else end=mid;
        }
        return nums[begin];
    }
};
```
## 总结
总体的思路还是二分法，不过注意细节处的区别
