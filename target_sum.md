# Target Sum
## Problem 
You are given a list of non-negative integers, a1, a2, ..., an, and a target, S. Now you have 2 symbols + and -. For each integer, you should choose one from + and - as its new symbol.

Find out how many ways to assign symbols to make sum of integers equal to target S.

Example 1:
Input: nums is [1, 1, 1, 1, 1], S is 3. 
Output: 5
Explanation: 

-1+1+1+1+1 = 3
+1-1+1+1+1 = 3
+1+1-1+1+1 = 3
+1+1+1-1+1 = 3
+1+1+1+1-1 = 3

There are 5 ways to assign symbols to make the sum of nums be target 3.
Note:
The length of the given array is positive and will not exceed 20.
The sum of elements in the given array will not exceed 1000.
Your output answer is guaranteed to be fitted in a 32-bit integer.
## 解题思路
给定数组和目标值，对每一个元素取正或取负，找相加得到返回值的方案的个数</br>
为写起来简洁，我把获得个数的代码写成一个函数，运用了递归的思想：具体思路就是遍历将目标值与element相加或相减，判断标志为下标达到nums.size且目标值等于0
## 编程实现
```C++
class Solution {
public:
    void getRes(vector<int>& nums,int i,int s,int& res)
    {
        if(i==nums.size()&&s==0)
        {
            res++;
            return ;
        }
        else if(i<nums.size()){
            getRes(nums,i+1,s-nums[i],res);
            getRes(nums,i+1,s+nums[i],res);
        }
    }
    int findTargetSumWays(vector<int>& nums, int S){
        int res=0;
        getRes(nums,0,S,res);
        return res;
    }
};
```
