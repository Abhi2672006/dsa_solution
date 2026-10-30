# solution dp +memoization
```cpp
class Solution {
public:
int count=0;

    int  decode(int i,int n,string& s,vector<int>& memo){
      
        if(i==n){
            
            return 1;
        }
        if(s[i]=='0') return 0;
        if(memo[i]!=-1) return memo[i];
        int a=decode(i+1,n,s,memo);
        
        int b=0;
        if(i+1<n){
            int two=(s[i]-'0')*10+(s[i+1]-'0');
            if(two<=26){
                b=decode(i+2,n,s,memo);
            }
        }
        return memo[i]=a+b;
        

    }
    int numDecodings(string s) {
        int n=s.size();
        vector<int> memo(n,-1);
         return decode(0,n,s,memo);
    }
};
```
## complexity
**time:**O(n)
**Space:**O(n)

# solution space optimization
```cpp
class Solution {
public:
    int numDecodings(string s) {
        int next1=1;
        int next2=0;

        int curr;
        int n=s.size();
        int two;
        for(int i=n-1;i>=0;i--){
            curr=0;
            if(s[i]!='0'){
                curr=next1;
                if(i+1<n){
                    two=(s[i]-'0')*10+(s[i+1]-'0');
                    if(two<=26){
                        curr+=next2;
                    }
                }
            }
            next2=next1;
            next1=curr;
        }
        return next1;
    }
};
```
## complexity
**time:**O(n)
**Space:**O(1)