# Solution Two pointer
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {
        int n=numbers.size();
        int left=0;
        int right=n-1;
        int sum;
        while(left<right){
            sum=numbers[left]+numbers[right];
            if(sum==target){
                return {left+1,right+1};
            }
            else if(sum>target){
                right--;
            }
            else{
                left++;
            }

        }
        return {};
    }
};
```
## Complexity
- **Time:** O(n)
- **Space:** O(1)