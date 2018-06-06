## problem 
Given an integer, write a function to determine if it is a power of two.

Example 1:

Input: 1
Output: true 
Explanation: 20 = 1
Example 2:

Input: 16
Output: true
Explanation: 24 = 16
Example 3:

Input: 218
Output: false
## 解题思路
开始用了最简单的循环来做，可惜超时了，然后看到一种超级简单的位运算的方法

## 代码实现
超时
```
class Solution {
public:
    bool isPowerOfTwo(int n) {
        if(n==1)
            return true;
        int temp=1;
        for(int i=1;temp<=n;i++){
            temp=temp*2;
            if(temp==n)
                return true;
        }
        return false;
    }
};
```
AC
```C++
class Solution {
public:
    bool isPowerOfTwo(int n) {
        if(n<=0)
            return false;
        return (n&(n-1))==0;
    }
};
```
