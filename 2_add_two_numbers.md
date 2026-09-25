# Solution 
```cpp
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode dummy(0);
        int carry=0;
        ListNode* temp=&dummy;
        int sum;
        int a,b;
        while(l1 || l2){
            a=(l1!=NULL) ? l1->val:0;
            
            b=(l2!=NULL) ? l2->val:0;
          
            sum=a+b+carry;
           
            temp->next=new ListNode(sum%10);
            if((sum)>9){
                carry=1;
            }
            else{
                carry=0;
            }
            temp=temp->next;
            if(l1!=NULL)  l1=l1->next;
            if(l2!=NULL)  l2=l2->next;
            
        }
      
        
            if(carry==1){
                temp->next=new ListNode(1);
            }
            return dummy.next;
        
    }
};
```
## Complexity
- **Topic:**Linked List
- **Time:**O(max(m,n));
- **Space:**O(max(m,n));