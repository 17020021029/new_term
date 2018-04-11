# Integer Break
## Problem
Given a positive integer n, break it into the sum of at least two positive integers and maximize the product of those integers. Return the maximum product you can get.

For example, given n = 2, return 1 (2 = 1 + 1); given n = 10, return 36 (10 = 3 + 3 + 4).

Note: You may assume that n is not less than 2 and not larger than 58.
## 问题分析
找到和为n的数组的乘积的最大值
## 编程实现
```C++
class Solution {
public:
    int integerBreak(int n) {
        int max;
        if(n==2) return 1;
        if(n==3) return 2;
        if(n%3 == 1) 
            return pow(3,((n-4)/3))*4;
        else if(n%3 == 2)
            return pow(3,(n/3))*2;
        else  
            return pow(3,n/3);
    }
};
```
