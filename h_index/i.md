## problem
Given an array of citations (each citation is a non-negative integer) of a researcher, write a function to compute the researcher's h-index.

According to the definition of h-index on Wikipedia: "A scientist has index h if h of his/her N papers have at least h citations each, and the other N − h papers have no more than h citations each."

Example:

Input: citations = [3,0,6,1,5]
Output: 3 
Explanation: [3,0,6,1,5] means the researcher has 5 papers in total and each of them had 
             received 3, 0, 6, 1, 5 citations respectively. 
             Since the researcher has 3 papers with at least 3 citations each and the remaining 
             two with no more than 3 citations each, his h-index is 3.
Note: If there are several possible values for h, the maximum one is taken as the h-index.

## 解题思路
返回的是h数的最大值，所以不妨直接从大到小排序
## 编程实现
```C++
class Solution {
public:
    int hIndex(vector<int>& citations) 
    {
        sort(citations.rbegin(),citations.rend());
        int count=1;
        for(int i=0;i<citations.size();i++){
            if(citations[i]<count){
                return count-1;
            }
            count++;
        }
        return count-1;
    }
};
```
