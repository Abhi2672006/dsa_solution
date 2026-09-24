# Solution 1 recursion
```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    void list (ListNode*& head,int n,int& count){
        if(head==NULL) return;
        
        list(head->next,n,count);
        count++;
        if(n==count){
            head=head->next;
        }

    }
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        
        int count=0;
        list(head,n,count);
        return head;
    }
};
```
- **Topic:**recursion
- **Time:**O(L);
- **Space:**O(L) recursion stack;

# Solution 2 two pointer 
```cpp
class Solution {
public:
    
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        int count=0;
        ListNode* dummy=new ListNode(-1);
        dummy->next=head;
        
        ListNode* slow=dummy;
        ListNode* fast=dummy;;
        while(count<n && fast!=NULL){
            fast=fast->next;
            count++;
        }
        while(fast->next!=nullptr){
            slow=slow->next;
            fast=fast->next;
        }
        if(slow!=NULL && slow->next!=nullptr){
        slow->next=slow->next->next;
        }
        return dummy->next;
    }
};
```
- **Time:**O(L)
- **Space:**O(1)