## Problem
Say you have an array for which the ith element is the price of a given stock on day i.

Design an algorithm to find the maximum profit. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times).

Note: You may not engage in multiple transactions at the same time (i.e., you must sell the stock before you buy again).

Example 1:

Input: [7,1,5,3,6,4]
Output: 7
Explanation: Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5-1 = 4.
             Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6-3 = 3.

Example 2:

Input: [1,2,3,4,5]
Output: 4
Explanation: Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
             Note that you cannot buy on day 1, buy on day 2 and sell them later, as you are
             engaging multiple transactions at the same time. You must sell before buying again.

Example 3:

Input: [7,6,4,3,1]
Output: 0
Explanation: In this case, no transaction is done, i.e. max profit = 0.
## 代码实现
先看一下我自以为是的很厉害的解法，实际上不仅麻烦而且错误，后来发现是道easy题，这么简单的题我竟然一下子写不出来，简直混蛋！
#### Time Limited Error
```C++
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int res=0;
        bool is;
        int temp;
        for(int i=0;i<prices.size();i++){
            temp=res;
            if(is==0){
                is=1;
                buy(res,prices,i);
            }
            if(is==1&&res<=prices[i]){
                i=0;
                sell(res,prices,i);
            }
            res=max(res,temp);
        }
        return res;
    }
    void buy(int& res,vector<int>& prices,int idex){
        res+=prices[idex];
    }
    void sell(int& res,vector<int>& prices,int idex){
        res-=prices[idex];
    }
};
```
#### AC
```C++
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int res=0;
        if(prices.size()<=1)
            return 0;
        for(int i=0;i<prices.size()-1;i++){
            if(prices[i]<prices[i+1])
                res+=prices[i+1]-prices[i];
        }
        return res;    
    }
};
```
