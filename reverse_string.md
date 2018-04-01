# Reverse String 
## problem 
Write a function that takes a string as input and returns the string reversed.

Example:
Given s = "hello", return "olleh". 
## 问题分析
Write a function that takes a string as input and returns the string reversed.

Example:
Given s = "hello", return "olleh". 
## 解题思路
二分法,遍历，交换当前最前和最后的
## 代码实现
```C++
class Solution {
public:
    string reverseString(string s) {
        int len=s.size();
        int begin=0;
        int end=len-1;
        while(begin<end)
        {
            swap(s[begin],s[end]);
            end--;
            begin++;
        }
        return s;
    }
};
```
## 总结
面向对象真的好用
