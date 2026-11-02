# Solution one 
```cpp
class Solution {
public:
    bool checkInclusion(string s1, string s2) {
        vector<int> ch(26,0);
        int n=s1.size();
        for(int i=0;i<s1.size();i++){
            ch[s1[i]-'a']++;
        }
        int j;
        int m=s2.size();
        vector<int> ch2=ch;
        for(int i=0;i<m-n+1;i++){
            if(ch[s2[i]-'a']==0) continue;
          
            for(j=i;j<i+n;j++){
                if(ch[s2[j]-'a']){
                    ch[s2[j]-'a']--;
                     
                }
                else{
                    break;
                }
                
            }
            ch=ch2;
            if(j==i+n){
            return true;
            }
        }
        return false;
    }
};
```
## Complexity
**Time:**O(n)
**Space:**O(n)

# solution sliding window
```cpp
class Solution {
public:
    bool checkInclusion(string s1, string s2) {
        int n=s1.size();
        int m=s2.size();
        if(n>m) return false;
        vector<int> need(26,0), win(26,0);
        for(auto& c:s1) need[c-'a']++;
        
        for(int i=0;i<m;i++){
            win[s2[i]-'a']++;
            if(i>=n) win[s2[i-n]-'a']--;
            if(need==win)return true;
        }
        return false;
    }
};
```
## Complexity
**Time:**O(n)
**Space:**O(n);