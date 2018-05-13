## problem

Given an array of citations in ascending order (each citation is a non-negative integer) of a researcher, write a function to compute the researcher's h-index.

According to the definition of h-index on Wikipedia: "A scientist has index h if h of his/her N papers have at least h citations each, and the other N − h papers have no more than hcitations each."

Example:

Input: citations = [0,1,3,5,6]
Output: 3 
Explanation: [0,1,3,5,6] means the researcher has 5 papers in total and each of them had 
             received 0, 1, 3, 5, 6 citations respectively. 
             Since the researcher has 3 papers with at least 3 citations each and the remaining 
             two with no more than 3 citations each, his h-index is 3.
Note: If there are several possible values for h, the maximum one is taken as the h-index.
## 解题思路
看似一样的题，但是相同的代码放上去会超时，一般这样可以采用二分法
## 代码实现
```C++
class Solution {
public:
        int hIndex(vector<int>& citations) 
        {
        int n = citations.size();
        int begin = 0;
        int end = n;
        while(begin < end){
            int mid = (end - begin) / 2 + begin;
            if(citations[mid] < n - mid) begin = mid + 1;
            else end = mid;
        }
        return n - end;
        }
};
```
