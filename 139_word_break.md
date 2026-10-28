# Solution 1 visited array + stack
```cpp
class Solution {
public:
    bool wordBreak(string s, vector<string>& wordDict) {
        stack<int> t;
        int n=s.size();
        vector<bool> v(n+1,false);
        bool k;
        t.push(0);
        v[0]=true;
        int top;
        while(!t.empty()){
            top=t.top();
            t.pop();
            if(top==n) return true;
            for(auto& it:wordDict){
                int len=it.size();

                    if(top+len<=n && s.compare(top,len,it)==0){
                        if(!v[top+len]){
                        t.push(top+len);
                        v[top+len]=true;
                        }
                    }

                }
            }
        
        return false;
    }
};
```
// we can solve this question without using visited array but it can lead to tle on leetcode
 
 ## complexity 
 Time	O(n · m · L)
Space	O(n)

# Solution two dp
```cpp
class Solution {
public:
    bool wordBreak(string s, vector<string>& wordDict) {
        int n=s.size();
        unordered_set<string> words(wordDict.begin(),wordDict.end());
        vector<int> dp(n+1,false);
        dp[0]=true;
        for(int i=1;i<=n;i++){
            for(int j=0;j<i;j++){
                if(dp[j] && words.count(s.substr(j,i-j))){
                    dp[i]=true;
                    break;
                }
            }
        }
        return dp[n];
    }
};
```

## complexity
Time	O(n³)
Space	O(n + m·L)
