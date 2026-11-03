# Solution recursion brute force
```cpp
class Solution {
public:
    int count=0;
    void find(int ind,int res,int amount,vector<int>& coins,int n){
        if(res==amount){   
            count++;
            return;
        }
        for(int i=ind;i<n;i++){
            if(res+coins[i]>amount) break;
            find(i,res+coins[i],amount,coins,n);
        }
    }
    int change(int amount, vector<int>& coins) {
        sort(coins.begin(), coins.end()); 
        int n=coins.size();
        find(0,0,amount,coins,n);
        return count;
    }
};
```
## Complexity
**Time:** Exponential
**Space:** O(amount/min coin) stack
It just give tle on leetcode

# Solution Dp memoization
```cpp
class Solution {
public:
   int  find(int ind,int rem,vector<vector<int>>& dp,int n,vector<int>& coins){
        if(rem==0) return 1;
        if(ind==n) return 0;
        if(dp[ind][rem]!=-1) return dp[ind][rem];
        int take=0;
        if(coins[ind]<=rem){
            take=find(ind,rem-coins[ind],dp,n,coins);
        }
        int skip=find(ind+1,rem,dp,n,coins);
        return dp[ind][rem]=take+skip;

    }
    int change(int amount, vector<int>& coins) {
        int n=coins.size();
        vector<vector<int>> dp(n,vector<int> (amount+1,-1));

        return find(0,amount,dp,n,coins);
       
    }
};

```
