# Solution stack
```cpp
class Solution {
public:
    int evalRPN(vector<string>& tokens) {
        stack<int> s;
        int n=tokens.size();
        int a;
        int b;
        for(int i=0;i<n;i++){
            if(tokens[i]=="+" || tokens[i]=="-" || tokens[i]=="*" || tokens[i]=="/"){
                b=s.top();
                s.pop();
                a=s.top();
                s.pop();
                char c=tokens[i][0];
                switch(c){
                    case '+':
                        s.push(a+b);
                        break;
                    case '-':
                        s.push(a-b);
                        break;
                    case '*':
                        s.push(a*b);
                        break;
                    case '/':
                        s.push(a/b);
                        break;
                    default:
                        break;
                }
            }
            else{
                s.push(stoi(tokens[i]));
            }

        }
        return s.top();
    }
};
```
## complexity 
- **Time :** O(n)
- **Space:** O(n)