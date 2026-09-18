# Solution one
```cpp
class Solution {
public:
    bool isValid(string s) {
        stack<char> a;
        char a_top;
        for(int i=0;i<s.size();i++){

            if(s[i]=='(' || s[i]=='{' ||s[i]=='['){
                a.push(s[i]);
                continue;
            }
            
            switch(s[i]){
                case ')':
                    if(!a.empty() && a.top()=='(') a.pop();
                     else return false;
                    break;
                case '}':
                    if(!a.empty() && a.top()=='{') a.pop();
                     else return false;
                    break;
                case ']':
                    if(!a.empty() &&  a.top()=='[') a.pop();
                    else return false;
                    break;
                default:
                    return false;
                    break;
            }
            
            

       
        }
         if(a.empty()) return true;
         return false;
    }
};
```
 ## Complexity
 - **Time :** O(n)
 - **Space:** O(n)