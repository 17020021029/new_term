# Linked List Cycle
## Problem
Given a linked list, determine if it has a cycle in it.

Follow up:
Can you solve it without using extra space?

## 解题思路
遍历linked list，同时用个set进行记录遍历过的节点，如果遍历linked list时发现当前节点已经在set中出现过了。那就说明成环了。set将使用O(N)的空间复杂度。
 但是，题目要求不用extra space。所以可以考虑两个指针first, second在linked list上遍历，一个跑得快，一个跑得慢。如果linked list成环，那么慢指针终将被快指针追上。
## 代码实现
```C++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    bool hasCycle(ListNode *head) {
        ListNode* p1=head,*p2=head;
        while(p2&&p2->next){
            p2=p2->next->next;
            p1=p1->next;
            if(p1==p2)  return true;
        }
        return false;
    }
};
```
