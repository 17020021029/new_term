## problem
You are standing at position 0 on an infinite number line. There is a goal at position target.

On each move, you can either go left or right. During the n-th move (starting from 1), you take n steps.

Return the minimum number of steps required to reach the destination.

Example 1:
Input: target = 3
Output: 2
Explanation:
On the first move we step from 0 to 1.
On the second step we step from 1 to 3.
Example 2:
Input: target = 2
Output: 3
Explanation:
On the first move we step from 0 to 1.
On the second move we step  from 1 to -1.
On the third move we step from -1 to 2.

## 解题思路
好久才明白是每一步都是相应的步数 ，但是解法还是不对，按照我都解法，2的时候一直不能走到target
```
class Solution {
public:
    int reachNumber(int target) {
        int res=1;
        int current=0;
        while(current!=target){   
            if(current<target){
                current+=res;
            }
            else if(current>target){
                current-=res;
            }
            res++;
        }
        return res-1;
    }
};
看到第二个ex，意识到是要输出最小值的,按上边的算法，一直走不到target，其实找规律可以看出来如果一直靠近target（有可能是负值）的话，若最后的左边距离target是偶数，则上一步倒回去，再加上的话，就是taget，所以，这时候就是最后加的步数
,若是奇数的话，是k+1+(k%2)
```

## 代码实现
```C++
class Solution {
public:
    int reachNumber(int target) {
        target=abs(target);
        int k=0;
        int current=0;
        while(current<target){
            current+=(++k);
        }
        int temp=current-target;
        if(temp%2==0)
            return k;
        return k+1+(k%2);
    }
};
```
