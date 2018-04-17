# rotated list
## problem

## 代码实现
 ```C
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
ListNode *rotateRight(ListNode *head, int k) 
     {
        if(head == NULL || head->next == NULL||k==0) return head;
        ListNode* node = head;
        int size =1; 
        while(node->next != NULL)
        {
            size++;
            node = node->next;
        }
        node->next=head;
        k = k%size;
        while(--size >= k)
        {
            node=node->next;
        }
        ListNode* first = node->next;
        node->next=NULL;   
        return first;
    }
};
```
