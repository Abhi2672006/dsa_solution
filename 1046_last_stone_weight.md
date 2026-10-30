# Solution priority queue min heap
```cpp
class Solution {
public:
    int lastStoneWeight(vector<int>& stones) {
        priority_queue<int> pq;
        for(int x:stones){
            pq.push(x); //O(logn)x n
        }
        int a,b;
        while(pq.size()>1){
            a=pq.top();
            pq.pop();
          
            b=pq.top();
            pq.pop();
            
            
            pq.push(a-b);
        }
        if(!pq.empty()) return pq.top();
        return 0;
    }
};
```
## Complexity
**time:** O(nlogn)
**Space:**O(n)
