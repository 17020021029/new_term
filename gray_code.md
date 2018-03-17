# Gray Code
## Problem
The gray code is a binary numeral system where two successive values differ in only one bit.

Given a non-negative integer n representing the total number of bits in the code, print the sequence of gray code. A gray code sequence must begin with 0.

For example, given n = 2, return [0,1,3,2]. Its gray code sequence is:
````
00 - 0
01 - 1
11 - 3
10 - 2
````
Note:
For a given n, a gray code sequence is not uniquely defined.

For example, [0,2,3,1] is also a valid gray code sequence according to the above definition.

For now, the judge is able to judge based on one instance of gray code sequence. Sorry about that.
## 问题分析
开始我觉得很麻烦，要通过遍历每一位上的情况，再遍历计算其十进制的结果；但是后来看到discuss里边全是通过按位运算符完成的
## 代码实现
```C++
class Solution {
public:
    vector<int> grayCode(int n) {
        vector<int> res(1<<n);  //开辟（1<<n)的存储空间，相当于1*n个
        for(int i=0;i<(1<<n);i++)
        {
            res[i]=i^(i>>1);  //相当于i-i/2的运算
        }
        return res;
    }
};
```
