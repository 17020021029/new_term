# Median of Two Sorted Arrays
## problem
There are two sorted arrays nums1 and nums2 of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

Example 1:
nums1 = [1, 3]
nums2 = [2]

The median is 2.0
Example 2:
nums1 = [1, 2]
nums2 = [3, 4]

The median is (2 + 3)/2 = 2.5
## 解题思路
一道hard题，但是感觉很简单啊，和数组一样处理，只不过用了几个算法
## 代码实现
```C++
class Solution {
public:
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        double median = 0;
        nums1.insert(nums1.end(), nums2.begin(), nums2.end());
        sort(nums1.begin(),nums1.end());
        if(nums1.size()%2==1)
        median = (double) nums1.at((nums1.size()/2));
        else
        {
            double n1 = (double) nums1.at((nums1.size()/2));
            double n2 = (double) nums1.at((nums1.size()/2)-1);
            median = (n1+n2)/2;
        }
        return median;
    }
};
```
