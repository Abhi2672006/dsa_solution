# Solution greedy
```cpp
class Solution {
public:
    int canCompleteCircuit(vector<int>& gas, vector<int>& cost) {
        int total=0;
        int tank=0;
        int diff=0;
        int start;
        for(int i=0;i<gas.size();i++){
            diff=gas[i]-cost[i];
            total+=diff;
            tank+=diff;
            if(tank<0){
                start=i+1;
                tank=0;
            }
        }
        return (total>=0)?start:-1;
    }
};
```
