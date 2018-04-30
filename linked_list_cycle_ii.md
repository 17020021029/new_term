# Linked List Cycle II
## problem
Given a linked list, return the node where the cycle begins. If there is no cycle, return null.

Note: Do not modify the linked list.

Follow up:
Can you solve it without using extra space?

## 解题思路
[参考资料](https://blog.csdn.net/willduan1/article/details/50938210)
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
    ListNode *detectCycle(ListNode *head) {
        ListNode* p1=head,*p2=head;
        while(p2&&p2->next){
            p2=p2->next->next;
            p1=p1->next;
            if(p1==p2)
                break;
        }
        if(p2==NULL||p2->next==NULL){
            return NULL;
        }
        p1=head;
        while(p1!=p2){
            p1=p1->next;
            p2=p2->next;
        }
        return p1;
    }
};
```
## 反思
快慢指针的运用

还有类似的题，可以再练习
