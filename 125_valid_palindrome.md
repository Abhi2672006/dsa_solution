# Solution one using extra space
```cpp
class Solution {
public:
    bool isPalindrome(string s) {
        int n=s.size();
        string a;
        char c;
        for(int i=0;i<n;i++){
            if(!isalnum(s[i])) continue;
            c=tolower(s[i]);
            a.push_back(c);
        }
        cout<<endl;
        int left=0;
        int right=a.size()-1;
        while(left<=right){
            if(!(a[left]==a[right])) return false;
          
            left++;
            right--;
        }
        return true;

    }
};
```
## Complexity
- **Time Complexity:**O(n)
- **Space Complexity:**O(n)

# Solution two space complexity O(1)
```cpp
class Solution {
public:
    bool isPalindrome(string s) {
        int n=s.size();
        string a;
        char c;
        for(int i=0;i<n;i++){
            if(!isalnum(s[i])){
                s[i]=' ';
                continue;
                }
            s[i]=tolower(s[i]);
         
           
        }
    
        int left=0;
        int right=s.size()-1;
        while(left<=right){
            if(s[left]==' '){
                left++;
                continue;
            }
            if(s[right]==' '){
                right--;
                continue;
            }
            
            if(!(s[left]==s[right])) return false;
          
            left++;
            right--;
        }
        return true;

    }
};
```
## Complexity
- **Time Complexity:**O(n)
- **Space Complexity:**O(1)