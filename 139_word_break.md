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
                if(dp[j] && words.count(s.substr(j,i-j))){ // here we are trying to check that if i=4 and string is leetcode now we are checking dp is true or not because we only check that from j to i is a word in dictionary or not when we assure that before j all are separable like for example i is on last e in `leetcode` so j is 0 means l so we check is dp[0] is true or not and it is true so we check that is that word from j to i is in dictionary and the that word is leetcode the answer is no then j=1 which is false j=2 false j=3 dp false but j=4 it is true and it is changed when we are checking for word leet so we check the string from j to i whcih is code as a word in dictionary which is true so dp[i]=true  
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
