# Divide Two Integers
## problem 
Given two integers dividend and divisor, divide two integers without using multiplication, division and mod operator.

Return the quotient after dividing dividend by divisor.

The integer division should truncate toward zero.

Example 1:

Input: dividend = 10, divisor = 3
Output: 3
Example 2:

Input: dividend = 7, divisor = -3
Output: -2
Note:

Both dividend and divisor will be 32-bit signed integers.
The divisor will never be 0.
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−231,  231 − 1]. For the purpose of this problem, assume that your function returns 231 − 1 when the division result overflows.
## 问题分析
两数相除但是不能使用除法乘法和取余运算,根据除法的基本原理结合递归
## 编程实现
```C++
class Solution {
public:
    int divide(int dividend, int divisor) {
        long long res=0;
        long long m=abs((long long)dividend),n=abs((long long)divisor);
        long long t=n,p=1;
        if(m<n) return 0;
        while(m>(t<<1)) 
        {
            t<<=1;
            p<<=1;
        }
        res+=p+divide(m-t,n);
        if((dividend<0)^(divisor<0))
        res=-res;
        return res>INT_MAX ? INT_MAX : res;
    }
};

```

## 反思
重新刷了这道题，发现只需要考虑极限的情况就好了
```C++
class Solution {
public:
    int divide(int dividend, int divisor) {
        if(divisor==0||(dividend==INT_MIN&&divisor==-1))
            return INT_MAX;
        else{
            return int(dividend/divisor);
        }
    }
}; 
```
