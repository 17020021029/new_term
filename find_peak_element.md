# Find Peak Element
## Problem
A peak element is an element that is greater than its neighbors.

Given an input array where num[i] ≠ num[i+1], find a peak element and return its index.

The array may contain multiple peaks, in that case return the index to any one of the peaks is fine.

You may imagine that num[-1] = num[n] = -∞.

For example, in array [1, 2, 3, 1], 3 is a peak element and your function should return the index number 2.

click to show spoilers.
## 问题分析
最简单的就是遍历整个数组，找到peak，优化一点，就是用而二分法
## 代码实现
```C++
 class Solution {
public:
    int findPeakElement(const vector<int> &num) {
        int left = 0;
        int right = num.size()-1;
        while(left<right){
            int mid = (right+left)/2;
            if(num[mid]<num[mid+1]){
                left = mid+1;
            }
            else right = mid;
        }
        return right;
    }
};
```
