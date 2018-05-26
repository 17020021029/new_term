## problem
Write a program to find the n-th ugly number.

Ugly numbers are positive numbers whose prime factors only include 2, 3, 5. 

Example:

Input: n = 10
Output: 12
Explanation: 1, 2, 3, 4, 5, 6, 8, 9, 10, 12 is the sequence of the first 10 ugly numbers.
Note:  

1 is typically treated as an ugly number.
n does not exceed 1690.
## 解题过程
最开始的思路是遍历，按照unlt number I的算法将所有的ugly number push到容器中，最后返回第n个容器中的元素,但是这做会超时</br>
超时代码
 ```C++
 class Solution {
public:
    bool isugly(int i){
        while(i%2==0)i/=2;
        while(i%3==0)i/=3;
        while(i%5==0)i/=5;
        if(i==1)
            return true;
        return false;
    }
    int nthUglyNumber(int n) {
        vector<int> ugly;
        int count=0;
        int i=0;
        while(count<=n){
            i++;
            if(isugly(i)){
                ugly.push_back(i);
                count++;
            }
        }
        return ugly[n-1];
    }
};
```
[正解](https://www.cnblogs.com/grandyang/p/4743837.html)
```C++
class Solution {
public:
    int nthUglyNumber(int n) {
        vector<int> res(1,1);
        int i2=0,i3=0,i5=0;
        while(res.size()<n){
           int m2=res[i2]*2,m3=res[i3]*3,m5=res[i5]*5;
            int mn=min(m2,min(m3,m5));
            if(mn==m2)i2++;
            if(mn==m3)i3++;
            if(mn==m5)i5++;
            res.push_back(mn);
        }
        return res.back();
    }
};
```
