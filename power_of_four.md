# Power of Four
## problem
Given an integer (signed 32 bits), write a function to check whether it is a power of 4.

Example:
Given num = 16, return true. Given num = 5, return false.

Follow up: Could you solve it without loops/recursion?

//判断整数是否为4的整数幂

## 问题分析
第一遍实现，很简单的操作，不过没有考虑到num=1的情况，但是改掉后，超时，回头看了一眼才发现不让用循环和递归，那肯定不是这么简单的操作就能完成的</br>
```
class Solution {
public:
    bool isPowerOfFour(int num) {
        if(num==1)
            return true;
        int tmp=1;
        while(tmp<=num)
        {
            tmp=tmp*4;
            if(tmp==num)
                return true;
        }
        return false;
    }
};
```
## 代码实现
直接枚举所有情况AC
```C++
class Solution {  
public:  
    bool isPowerOfFour(int num) {  
        if(num == 1)
            return true;  
        if(num%2==1)
            return false;  
        if(num <= 0)
            return false;  
        if(num%4 != 0)
            return false;  
        if(num/4==1) 
            return true;  
        return isPowerOfFour(num/4);  
    }  
};  
```
看到有位运算的解法，但是我位运算确实不怎么会，直接贴一下代码好了
```C++
class Solution {  
public:  
    bool isPowerOfFour(int num) {  
        if(num <= 0) return false;  
        if(num & num-1) return false;  
        return num % 3 == 1;  
    }  
};  
```
