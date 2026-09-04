# 121 Best Time to buy and sell stock

## Iterative solution two pointer
```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int min=INT_MAX;
        int maxi=0;
        for(int i=0;i<prices.size();i++){
            if(prices[i]<=min){
                min=prices[i];
                }
            else{
                maxi=max(prices[i]-min,maxi);
                }}
        return maxi;
    }
};
```
### Complexity
- **Time Complexity:**O(n)
- **Space Complexity:**O(1)

## Compressed DP

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int profit=0;
        int mini=prices[0];
        int cost;
        for(int i=1;i<prices.size();i++){
            cost=prices[i]-mini;
            profit=max(cost,profit);
            mini=min(mini,prices[i]);
        }
        return profit;
    }
};
```
- **Time Complexity:**O(n)
- **Space Complexity:**O(1)