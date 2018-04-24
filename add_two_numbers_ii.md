# Add Two Numbers II
[Add Two Numbers](https://github.com/17020021029/leetcode/blob/master/add_two_numbers.md)
## problem
You are given two non-empty linked lists representing two non-negative integers. The most significant digit comes first and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

Follow up:
What if you cannot modify the input lists? In other words, reversing the lists is not allowed.
## 解题思路
因为这次是倒叙相加的，考虑到这一点，我们可以用栈来实现，先进后出；</br>
从链表后边往前加，即从栈顶开始加，加一个删除栈顶，不断更新头指针，是指针一直往前意味移动，保证先相加的放在链表尾部</br>
最后还要判断一下是否进位
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
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        stack<int> s1,s2;   //用栈,解决倒叙的问题
        while(l1){
            s1.push(l1->val);
            l1=l1->next;
        }
        while(l2){
            s2.push(l2->val);
            l2=l2->next;
        }
        int sum=0;
        ListNode* res=new ListNode(0);
        while(!s1.empty()||!s2.empty())
        {
            if(!s1.empty()){
                sum+=s1.top();
                s1.pop();
            }
            if(!s2.empty()){
                sum+=s2.top();
                s2.pop();
            }
            res->val=sum%10;
            ListNode* head=new ListNode(sum/10);
            head->next=res;
            res=head;
            sum/=10;
        }
        return res->val==0?res->next:res;   //是否有进位
    }
};
```
