# Solution 1 dp tabulation (bottom up)
```cpp
class Solution {
public:
    int lengthOfLIS(vector<int>& nums) {
        int n=nums.size();
        vector<int> dp(n,1);
        for(int i=1;i<n;i++){
            for(int j=0;j<i;j++){
                if(nums[i]>nums[j]){
                    dp[i]=max(dp[i],dp[j]+1);
                }
            }
        }
         return *max_element(dp.begin(), dp.end());
    }
};
```
10 9 2 5 7 3 101 18
 1 1 1 2 3 2   4  4
<!-- Here in this solution for each element in nums we are finding the longest substring till that element like for 10 there is no smaller element than 10 so the longest chain is one same for 7 there are are two elements smaller 2 and 5 longest chain of two is 1 and 5 is 2 so we take 5-2 so longest increasing chain till 7 is 3 -->

## complexity
**Time:** O(n*n)
**Space:**O(n)
# Solution two binary search+ greedy approach
```cpp
class Solution {
public:
    int lengthOfLIS(vector<int>& nums) {
        vector<int> dp; // dp[k] = smallest tail of any increasing subsequence of length k+1
        for (int num : nums) {
            // first position where dp[pos] >= num (dp is always sorted)
            auto it = lower_bound(dp.begin(), dp.end(), num);
            if (it == dp.end()) {
                dp.push_back(num);  // num is bigger than all tails, so the longest length grows by 1
            } else {
                *it = num;          // num is a smaller tail for that length, better for future extensions
            }
        }
        return dp.size(); // only the LENGTH is the answer, not the contents
    }
};
```
## complexity
**Time:**O(nlogn);
**Space:**O(n);