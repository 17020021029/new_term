# Search in Rotated Array
## problem
Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

(i.e., 0 1 2 4 5 6 7 might become 4 5 6 7 0 1 2).

You are given a target value to search. If found in the array return its index, otherwise return -1.

You may assume no duplicate exists in the array.
## 问题分析
题意是给一个数组，剩余程序回将数组旋转，给定一个target，返回下标，否则返回-1</br>
遍历数组时可以用二分法实现，技巧是找到当前mid值，若大于最左边的值，则左边有序，若大于最右边的值，则右边有序
## 编程实现
```C++
class Solution {
public:
    int search(vector<int>& nums, int target) {
       int begin = 0,end = nums.size()-1;  
        int mid;  
        while(begin <= end){  
            mid = (start + end) / 2;  
            if(nums[mid] == target){  
                return mid;  
            }  
            else if(nums[mid] >= nums[begin]){  //中间元素大于最左边元素则其左边有序             
                if(target >= nums[start] && target <= nums[mid]){//目标位于左边  
                    end = mid - 1;  
                }  
                else{ //目标位于右边
                    begin = mid + 1;  
                }  
            }  
            else{  //中间元素小于最右边元素则其右边有序              
                if(target <= nums[end] && target >= nums[mid]){  //目标位于右边
                    begin = mid + 1;  
                }    
                else{  //目标位于左边
                    end = mid - 1;  
                }  
            }  
        }  
        return -1;  
    }  
};
```
## 总结体会
这道题感觉还是比较简单的，所以我觉得它作为一个medium题，一定是由原因的，干脆就不采用暴力的遍历，而是选用二分法。但在过程中还是因为许多小错误wa了好几次，大概是因为二分法还没有掌握很好
