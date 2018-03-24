# Merge Intervals
## problem 
Given a collection of intervals, merge all overlapping intervals.

For example,
Given [1,3],[2,6],[8,10],[15,18],
return [1,6],[8,10],[15,18]. 
## 问题分析
先对区间集排序，因为区间集是结构体，所以要自己定义sort函数，先把第一组放进要返回的区间集中，之后遍历，若当前区间集的最后一个集合的end值小于当前遍历的区间的start值，则直接把当前集合加到返回集中，否则，比较当前区间集最后一个的end值与当前区间的end值，赋大值

## 代码实现
```C++
/**
 * Definition for an interval.
 * struct Interval {
 *     int start;
 *     int end;
 *     Interval() : start(0), end(0) {}
 *     Interval(int s, int e) : start(s), end(e) {}
 * };
 */
class Solution {
public:
    vector<Interval> merge(vector<Interval>& intervals) {
        if(intervals.empty())//intervals为空
            return {};  
        sort(intervals.begin(),intervals.end(),[](Interval&a,Interval &b){return a.start<b.start;});
        vector<Interval> res{intervals[0]};
        for(int i=1;i<intervals.size();i++)
        {
            if(res.back().end<intervals[i].start)
            {
                res.push_back(intervals[i]);
            }
            else 
            {
                res.back().end=max(res.back().end,intervals[i].end);
            }
        }
        return res;
    }
};
```
## 总结
思路很简单，就是涉及到vector类的使用时还是会有难度，还是要了解vector类才好
