# Letter combination of a phone number

## Solution one recursion
```cpp
class Solution {
public:
    void f(int ind,int &n,vector<string> &s,string s1,string digits,unordered_map<int,string> &mp){
        if(ind==n){
            s.push_back(s1);
            return;
        }
        int index=digits[ind]-'0';
        
        for(int i=0;i<mp[index].size();i++){
            
            s1.push_back(mp.at(index)[i]);
            f(ind+1,n,s,s1,digits,mp);
            s1.pop_back();
        }
    }
    vector<string> letterCombinations(string digits) {
        vector<string> s;
        string s1;
        int n=digits.size();

        unordered_map<int,string> mp = {
            {2, "abc"},
            {3, "def"},
            {4, "ghi"},
            {5, "jkl"},
            {6, "mno"},
            {7, "pqrs"},
            {8, "tuv"},
            {9, "wxyz"}
        };
        f(0,n,s,s1,digits,mp);
        return s;


    }
};
```

## Complexity
- **Time Complexity:**O(n*4^n)
- **Space Complexity:**O(n*4^n) //including output
- **Auxiliary space:**O(n)