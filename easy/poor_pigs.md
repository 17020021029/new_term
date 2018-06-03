## problem
There are 1000 buckets, one and only one of them contains poison, the rest are filled with water. They all look the same. If a pig drinks that poison it will die within 15 minutes. What is the minimum amount of pigs you need to figure out which bucket contains the poison within one hour.

Answer this question, and write an algorithm for the follow-up general case.

Follow-up:

If there are n buckets and a pig drinking poison will die within m minutes, how many pigs (x) you need to figure out the "poison" bucket within p minutes? There is exact one bucket with poison.

## 解题思路
解法并不是固定在一维的，要是n只小猪，就要扩展到n维，这样的话，算出一只小猪一小时内能查多少个（x），n个小猪，则就能查x^n个，只要大于buckets值就好了

## 代码实现
```C++
class Solution {
public:
    int poorPigs(int buckets, int minutesToDie, int minutesToTest) {
        if(buckets<=1)
            return 0;
        int k=(minutesToTest/minutesToDie)+1;
        int i=1;
        while(i<=buckets){
            if(pow(k,i)>=buckets){
                return i;
            }
            i++;
        }
        return -1;
    }
};
```
