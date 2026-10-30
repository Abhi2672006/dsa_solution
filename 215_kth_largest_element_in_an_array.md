# solution priority queue min heap

```cpp
class Solution {
public:
    int findKthLargest(vector<int>& nums, int k) {
        priority_queue<int, vector<int>, greater<int>> pq;
        for(int x:nums){
            pq.push(x);
            if(pq.size()>k) pq.pop();
        }
        return pq.top();
    }
};
```
**Time:**O(nlogn)
**Space:**O(n);

<!--uses min head to store data in ascending order but maintaining its length to k to maintian the k th largest at the top push the number onto heap then if head size is greater then k remove top-->
