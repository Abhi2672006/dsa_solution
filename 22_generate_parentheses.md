# 22 Generate parentheses

## Solution one recursion backtracking
```cpp
class Solution {
public:
    void f(int open,int close,vector<string> &arr,int n,string &s){
        if(open==close && close==n){
            arr.push_back(s);
            return;
        }
        if(open<n){
            s.push_back('(');
            f(open+1,close,arr,n,s);
            s.pop_back();
        }ac
        if(close<open){
            s.push_back(')');
            f(open,close+1,arr,n,s);
            s.pop_back();
        }
        
    }
    vector<string> generateParenthesis(int n) {
        
        
        vector<string> arr;
        string s;
        f(0,0,arr,n,s);
        return arr;
    }
};
```
### complexity
- **Time Complexity:** O(n × Cₙ) where Cₙ is the nth Catalan number.
- **Space Complexity:** O(n) auxiliary space.

**Catalan Number:**$$ \boxed{C_n=\frac{1}{n+1}\binom{2n}{n}} $$