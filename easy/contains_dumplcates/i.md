# Contains Dumplicates 
## problem 
Given an array of integers, find if the array contains any duplicates.

Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.

Example 1:

Input: [1,2,3,1]
Output: true

Example 2:

Input: [1,2,3,4]
Output: false

Example 3:

Input: [1,1,1,3,3,4,3,2,4,2]
Output: true
## 代码实现
```C++
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        return nums.size()>set<int>(nums.begin(),nums.end()).size();
    }
};
```
## 总结
题目很简单，关键是用到了set的用法，学习巩固一下STL
