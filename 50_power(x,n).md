# 50 power(x,n)

## Solution one iterative

```cpp
double pow(double x,int n){
    long long N=n;

    if(N<0){
        x=1/x;
        N=-N; // due to this we used Long Long N because int range is -2147483648  to  2147483647 and we are make n positive if neg N=-2147483648 then if we make it positive then it value become  2147483648 which i out of the range of int

    }
    int result=1;
    while(N>0){
        if(N%2!=){
        result*=x;
        }
        x*=x;
        N=N/2;
    }
    return result;
}
```
### Complexity
- **Time complexity:**O(logn)
- **space Complexity**O(1)

## Solution Recursive
```cpp
class Solution {
public:
    double pow(double x, long long N,double result){
        if(N<1) return result;
        if(N%2!=0){
            result*=x;
        }
        return pow(x*x,N/2,result);
    }
    double myPow(double x, int n) {
        long long N=n;

        if(N<0){
            x=1/x;
            N=-N;
        }
        double result=1;
        return pow(x,N,result);
           
    }
};
```
### Complexity
- **Time Complexity:**O(logn)
- **Space Complexity**O(logn)
