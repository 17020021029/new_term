## Problem
 Your task is to calculate ab mod 1337 where a is a positive integer and b is an extremely large positive integer given in the form of an array.

Example1:

a = 2
b = [3]

Result: 8

Example2:

a = 2
b = [1,0]

Result: 1024

## 解题思路
要用到数学知识
1. a^b % 1337 = (a%1337)^b % 1337

2. xy % 1337 = ((x%1337) * (y%1337)) % 1337, 其中xy是一个数字如:45, 98等等

其中第一个公式可以用来削减a的值, 第二个公式可以将数组一位位的计算, 比如 12345^678, 首先12345可以先除余1337, 设结果为X, 则原式就可以化为: 

X^678 = ((X^670 % 1337) * (X^8 % 1337)) % 1337 = (pow((X^670 % 1337), 10) * (X^8 % 1337)) % 1337
## 代码实现
```C++
    class Solution {  
    public:  
        int superPow(int a, int k)  
        {  
            if(k ==0) return 1;  
            int ans = 1;  
            for(int i = 1; i <= k; i++) ans = (ans*a) %1337;  
            return ans;  
        }  
          
        int superPow(int a, vector<int>& b) {  
            if(b.empty()) return 1;  
            a = a%1337;  
            int lastBit = b.back();  
            b.pop_back();  
            return (superPow(superPow(a, b), 10) * superPow(a, lastBit))%1337;  
        }  
    };  
```
## 参考来源
[discuss](https://discuss.leetcode.com/topic/50489/c-clean-and-short-solution/2)

[csdn](https://blog.csdn.net/niuooniuoo/article/details/51878696)
