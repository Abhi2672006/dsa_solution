# Solution extra space
```cpp
class Solution {
public:
    void rotate(vector<vector<int>>& matrix) {
        int n=matrix.size();
        vector<vector<int>> v;
        vector<int> a;
        for(int i=0;i<n;i++){

            for(int j=n-1;j>=0;j--){
                a.push_back(matrix[j][i]);
            }
            v.push_back(a);
            a.clear();
        }
        matrix=v;
    }
};
```
## Complexity
**Time:** O(n*n)
**Space:**O(n*n)

# Solution 2 in place 
```cpp
class Solution {
public:

void rotate(vector<vector<int>>& matrix) {
    int n = matrix.size();
    for (int i = 0; i < n; i++)
        for (int j = i + 1; j < n; j++)
            swap(matrix[i][j], matrix[j][i]);   // transpose
    for (int i = 0; i < n; i++)
        reverse(matrix[i].begin(), matrix[i].end());  // reverse each row

    }
};

```
## Complexity
**Time:**O(n*n)
**Space:**O(1)