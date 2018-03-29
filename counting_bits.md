# Counting Bits
## Problem
Given a non negative integer number num. For every numbers i in the range 0 ≤ i ≤ num calculate the number of 1's in their binary representation and return them as an array.

Example:
For num = 5 you should return [0,1,1,2,1,2]. 
## 问题分析
题目的意思是给定一个数，返回0<i<num的所有的数的二进制数的1的个数
## 代码实现
Timed Limited Error
以为是这个算法过于简单，所以超时的，后来试了用位运算后的代码还不行之后，然后在自己IDE中试一下是不是算法的问题，发现还真是，是我在while循环中直接把i给改了，那这样著名复制啊!傻子！
```
class Solution {
public:
    vector<int> countBits(int num) {
        vector<int> res(num+1,0);
        int count=0;
        for(int i=1;i<num;i++)
        {
            while(i>0)  
            {
                if(i%2==1)
                    count++;
                i/=2;
            }
            res[i]=count;
            count=0;
        }
        return res;
    }
};
```
另外一个主要矛盾的错误代码
```
class Solution {
public:
    vector<int> countBits(int num) {
        vector<int> res(num+1,0);
        int count=0;
        res[0]=0;
        for(int i=1;i<num;i++)
        {
            while(i)
            {
                i=i&(i-1);
                count++;
            }
            res[i]=count;
            count=0;
        }
        return res;
    }
};
```
AC
```C++
class Solution {
public:
    vector<int> countBits(int num) {
        vector<int> res(num+1,0);
        int count=0;
        res[0]=0;
        for(int i=1;i<num+1;i++)
        {
            int t=i;  //用temp值进行计算
            while(t)
            {
                t=t&(t-1);
                count++;
            }
            res[i]=count;
            count=0;
        }
        return res;
    }
};
```
## 总结
期间出错的原因主要是，还是计算思想不行，在while循环里已经改掉的i值，下面以为没动将其作为下标,真的像个傻子一样，这时候可以把当前i值存储，或着令定义int来进行i的操作

还有，感觉这道题不应该是medium题
