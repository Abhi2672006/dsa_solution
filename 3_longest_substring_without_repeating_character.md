# solution
```cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int left=0;
        int right=0;
        int n=s.size();
        int len=0;
        int max_len=0;
      
        unordered_map<char,int> mp;
        while(right<n){
            if(mp.find(s[right])!=mp.end() && mp[s[right]]>=left){
               
                    left=mp[s[right]]+1;
                }
                   max_len=max(right-left+1,max_len);
            mp[s[right]]=right;
            right++;
            
            
        }
        
       
        return max_len; 
    }
};
```
## Complexity 
- **Time Complexity:**O(n)
- **space Complexity:**O(1)