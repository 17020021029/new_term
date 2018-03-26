# Sum of Two Intergers
## problem 
Calculate the sum of two integers a and b, but you are not allowed to use the operator + and -.

Example:
Given a = 1 and b = 2, return 3. 
## 问题分析
虽然是一道easy题，但是感觉很有意思，不让'+'和'-'，那么自然只能用逻辑运算符，但因为用不熟练，而且逻辑运算有时会比较节剩时间，所以还是很有价值的一道题
## 代码实现
```C++
class Solution {
public:
    int getSum(int a, int b) {
        int c; //进位
        while(b!=0)
        {
            c=(a&b)<<1;
            a=a^b;  //相加
            b=c;    //进位当作b再与a相加，直到进位不存在
        }
        return a;
    }
};
```
## 总结
[位运算实现加减乘除](https://blog.csdn.net/itismelzp/article/details/49621741)
