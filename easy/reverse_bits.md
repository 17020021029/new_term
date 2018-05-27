## problem
Reverse bits of a given 32 bits unsigned integer.

Example:

Input: 43261596
Output: 964176192
Explanation: 43261596 represented in binary as 00000010100101000001111010011100, 
             return 964176192 represented in binary as 00111001011110000010100101000000.
Follow up:
If this function is called many times, how would you optimize it?
## 解题思路
想再接触一下位运算，感觉这道题大家都用到了位运算
### 法一
模拟reverse interger的方法，不断将每一位的数加到value中去
```C++
class Solution {  
public:  
    uint32_t reverseBits(uint32_t n) {  
        uint32_t value = 0;  
        uint32_t mask = 1;  
        for (uint32_t i = 0; i < 32; ++i) {  
            value = (value<<1 )|((n&mask)>>i);  
            mask <<=1;  
        }  
        return value;  
    }  
};
```
### 法二
基本和上面一致。区别在于，第一种做法是每次移动mask。第二种做法是每次右移输入的数字本身，mask永远是1.
```C++
class Solution {  
public:  
    uint32_t reverseBits(uint32_t n) {  
        uint32_t value = 0;  
        for (uint32_t i = 0; i < 32; ++i) {  
            value = (value<<1 )|((n>>i) & 1);  
        }  
        return value;  
    }  
};
```
### follow up的用意
```C++
class Solution {  
public:  
    uint32_t reverseBits(uint32_t n) {  
        uint32_t x = n;  
        x = ((x & 0x55555555) << 1) | ((x & 0xAAAAAAAA) >> 1);  
        x = ((x & 0x33333333) << 2) | ((x & 0xCCCCCCCC) >> 2);  
        x = ((x & 0x0F0F0F0F) << 4) | ((x & 0xF0F0F0F0) >> 4);  
        x = ((x & 0x00FF00FF) << 8) | ((x & 0xFF00FF00) >> 8);  
        x = ((x & 0x0000FFFF) << 16) | ((x & 0xFFFF0000) >> 16);  
        return x;  
    }  
};  
```
## [参考](https://blog.csdn.net/feliciafay/article/details/44536827)
