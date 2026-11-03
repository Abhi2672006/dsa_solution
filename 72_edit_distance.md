# Solution memoization
```cpp
class Solution {
public:
    int find(int i,int j,string& s1,string& s2,vector<vector<int>>& dp){
        if(i<0) return j+1;
        if(j<0) return i+1;
        if(dp[i][j]!=-1) return dp[i][j];
        if(s1[i]==s2[j]) return find(i-1,j-1,s1,s2,dp);

        return dp[i][j]=1+min({find(i-1,j,s1,s2,dp),find(i,j-1,s1,s2,dp),find(i-1,j-1,s1,s2,dp)});
    }
    int minDistance(string word1, string word2) {
        int n=word1.size();
        int m=word2.size();
        vector<vector<int>> dp(n,vector<int>(m,-1));
        return find(n-1,m-1,word1,word2,dp);
    }
};
```
## Complexity
**Time:**O(n*m)
**Space:**O(n*m) + recursion stack


# solution dp +tabulation
```cpp
class Solution {
public:
   
    int minDistance(string a, string b) {
        int n=a.size();
        int m=b.size();
        
        vector<vector<int>> dp(n+1,vector<int>(m+1,-1));
         for (int i = 0; i <= n; i++) dp[i][0] = i;
        for (int j = 0; j <= m; j++) dp[0][j] = j;
        for(int i=1;i<=n;i++){
            for(int j=1;j<=m;j++){
                if(a[i-1]==b[j-1]){ // we are working on the one based index so we have to access with
                    dp[i][j]=dp[i-1][j-1];
                    
                    }
                    else{
                        dp[i][j]=1+min({dp[i][j-1],dp[i-1][j],dp[i-1][j-1]});
                    }


            }
        }
        return dp[n][m];
    }
};
```
**Time:**O(n*m)
**Space:**(n*m)
``` In this we created a N*M grid to solve this problem 

# Solution 3 space optimization
```cpp
class Solution {
public:
   
    int minDistance(string a, string b) {
        int n=a.size();
        int m=b.size();
        
        vector<int> prev(m+1),curr(m+1);
         for (int i = 0; i <= m; i++) prev[i]=i;
     
        for(int i=1;i<=n;i++){
            curr[0]=i;
            for(int j=1;j<=m;j++){
                if(a[i-1]==b[j-1]){ // we are working on the one based index so we have to access with i-1
                    curr[j]=prev[j-1];
                    
                    }
                    else{
                        curr[j]=1+min({curr[j-1],prev[j-1],prev[j]});
                    }


            }
            swap(prev,curr);
        }
        return prev[m];
    }
};
```
## Complexity
**Time:**O(n*m)
**Space:**(n)

Here in this solution we see that we only need the two rows frist and two we dont need a full n*m grid so we only create and used two rows so our space dropped down to n