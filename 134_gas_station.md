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
## Complexity
**Time:**O(n)
**Space:**O(n)

so tank=0; means inital we have no gas
total=0;
start=0;
:i=0 gas=1 cost=3 now tank=0+1-3=-2 means if i go to station 1 with tank which cost 3 i will go out of fuel so now start
:i=1 tank=0 from starting at 0 we cannot reach 1 so we try to start from 1 so at i=1 gas=2 and cost 4 means if i start from here i got in tank=0+2-4 =-2 means if i start from here icannot reach the next station
:i=2 here tank is 0 means till now we cannot start before 2 so try to check can we start on 2 here tank=0+3-5=-2 means no
:i=3 tank=0 gas=4 cost=1 so tank=0+4-1 =3 means if i start from here with fuel 4 i can reach station 5 tank=3
:i=4 tank=3 gas=5 cost =2 means tank=4-2+5 8 which i positive means we can reach to station 5 if we start from station 3 and at last total>=0 means if we start from any point we can reach all station if total <0 then it means we cannot clear the path 
