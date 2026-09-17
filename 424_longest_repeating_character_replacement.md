# Solution one 
```cpp
class Solution {
public:
    int characterReplacement(string s, int k) {
        int left=0,right=0;
        int max_freq=0;
        int hash[26]={0};
        int max_len=0;
        while(right<s.size()){
            hash[s[right]-'A']++;
            max_freq=max(max_freq,hash[s[right]-'A']);
            if(((right-left+1)-max_freq)>k){
                hash[s[left]-'A']--;
                left++;;
            }
            else{
                max_len=max(max_len,right-left+1);
               
             
               
            }
             right++;

        }
        return max_len;
    }
};
```
## Complexity
- **Time:**O(n)
- **Space:**O(1)