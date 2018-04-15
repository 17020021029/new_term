# search in a rotated array II
## Problem


    Follow up for "Search in Rotated Sorted Array":
    What if duplicates are allowed?

    Would this affect the run-time complexity? How and why?

Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

(i.e., 0 1 2 4 5 6 7 might become 4 5 6 7 0 1 2).

Write a function to determine if a given target is in the array.

The array may contain duplicates.
## 问题分析
题目承接上一个题目[search in a rotated array](https://github.com/17020021029/new_term/blob/master/search_int_rotated_array.md),但如果直接套用之前的代码，就会出错，因为这个有很多重复元素,就会出现很多复杂的情况

例如，中间和边缘相等，那么不知道该怎么办，那么我们就令边缘逐渐靠近中间，直到不相等或相遇，在原来的代码上稍加改动，将之前判断两边是否有序时的边缘与中间相等情况去掉，在加上一个start++的判定条件
## 编程实现
```C++
class Solution {
public:
    int search(vector<int>& nums, int target) {
       int start = 0,end = nums.size()-1;  
        int mid;  
        while(start <= end){  
            mid = (start + end) / 2;  
            if(nums[mid] == target){  
                return true;  
            }  
            else if(nums[mid] > nums[start]){  //中间元素大于最左边元素则左部分为有序数组              
                if(target >= nums[start] && target <= nums[mid]){//目标位于左部分  
                    end = mid - 1;  
                }  
                else{ //目标位于右部分  
                    start = mid + 1;  
                }  
            }  
            else if(nums[mid]<nums[start]) {  //中间元素小于最右边元素则右部分为有序数组              
                if(target <= nums[end] && target >= nums[mid]){  //目标位于右部分  
                    start = mid + 1;  
                }    
                else{  //目标位于左部分 
                    end = mid - 1;  
                }  
            }
            else start++;
        }  
        return false;  
    }  
};
```
