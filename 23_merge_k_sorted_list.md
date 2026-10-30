# Solution priority queue min heap
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
    ListNode* mergeKLists(vector<ListNode*>& lists) {
       vector<int> vals;
for (ListNode* curr : lists)
    for (; curr; curr = curr->next) vals.push_back(curr->val);

priority_queue<int, vector<int>, greater<int>> pq(vals.begin(), vals.end());
        ListNode dummy(0);
        ListNode* tail = &dummy;

        while(!pq.empty()){
            tail->next=new ListNode(pq.top());
            pq.pop();
            tail=tail->next;

        }
        return dummy.next;
    }
};
```
<!--in this question we are first storing all the elements in a vector then adding them to min heap so the get sorted then creating a new single list for all the elements
-->