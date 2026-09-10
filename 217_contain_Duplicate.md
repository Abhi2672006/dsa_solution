# 217_contain_Duplicate

## Solution one

```cpp

class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        unordered_set<int> s;
        for(int i=0;i<nums.size();i++){
            if(!s.insert(nums[i]).second){ //in unordered_set insert returns a pair{iterator,bool} bool true if inserted false if already there
                
                return true;
            }
        }
        return false;
    }
};
```

### Complexity
- **Time Complexity:**O(n)
- **Space Complexity:**O(n)

## Solution 

```cpp
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        unordered_set<int> sum(nums.begin(),nums.end());
        if(nums.size()!=sum.size()) return true;
        return false;
    }
```
### Complexity
- **Time Complexity:**O(n)
- **Space Complexity:**O(n)