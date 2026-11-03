# Solution one greedy
```cpp

class Solution {
public:
    int jump(vector<int>& nums) {
        int jump=0;
        int farthest=0;
        int curr_end=0;
        int n=nums.size();

        for(int i=0;i<n-1;i++){ //from o to n-1 because we just have to check the last second element 
           
            farthest=max(farthest,nums[i]+i); //from current index how farthest we can go
             if(i==curr_end){// this is the boundary like our 0 2 is one jump and 2 to 4 is one jump 
                jump++;
                curr_end=farthest;
            }
        }
        return jump;

    }
};
```
## Complexity
**Time:**O(n)
**Space:**O(1)

# Solution 2 dp 
```cpp
class Solution {
public:
    int jump(vector<int>& nums) {
        int n=nums.size();
        vector<int> dp(n,INT_MAX);
        dp[0]=0;
       
        for(int i=1;i<n;i++){
            for(int j=0;j<i;j++){

            if(nums[j]+j>=i){
            dp[i]=min(dp[j]+1,dp[i]);
            }
           
        }}
        return dp[n-1];
    }
};
```
## Complexity
**Time:**O(n*n)
**Space:**O(n)

hey now we will understand the question
index:     0  1  2  3  4
value:     2  3  1  1  4
notebook: [0, 1, 1, 2, ?]
lets take this example like we what to find the value of notebook[4] so we will go to form j=0 to j=3 so 
1. j=0 index[0]=0,value[0]=2 so 0+2=2 which is not >=4 means we cannot reach to index 4
2. j=1 index[1]=3,so 1+3=4 which is >=4 means we can reach to index 4 but but now we will check that in how many steps we reached the index 1 which is number[1]=1 so we reach the index 1 in 1 step and from index 1 we will reach to index 4 in one step so total steps 1+1 =2 so **notebook[4]=2**
3. j=2 index[2]=1 so 2+1=3 which is not >=4 means we cannot reach to index 4
4. j=3 index[3]=1 so 3+1=4 which is >=4 means we can reach to index 4 now we will again check in how many steps we reached on index 3 whcih is notebook[3]=2 so to reach to index[3] we took 2 steps and from index 3 to index 4 we will take one step so total = 2+1 =3 but we already reached the index 4 in 2 steps so we will take the shortest which is 2 