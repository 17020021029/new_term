# Divide Two Integers
## problem 
Divide two integers without using multiplication, division and mod operator.

If it is overflow, return MAX_INT.

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
