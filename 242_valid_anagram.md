```cpp
class Solution {
public:
    bool isAnagram(string s, string t) {
        if(s.size()!=t.size()) return false;
        vector<int> l(26,0);
        for(int i=0;i<s.size();i++){
            l[s[i]-'a']++;
            l[t[i]-'a']--;
        }
        for(int i=0;i<26;i++){
            if(l[i]!=0) return false;
        }
        return true;
    }
};
```
## Complexity
- **Time Complexity**:O(n)
- **Space Complexity**:O(1)