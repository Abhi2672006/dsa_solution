# Solution
```cpp
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        int n=matrix.size();
        int m=matrix[0].size();
        vector<int> v;
        int top,bottom,left,right;
        top=0;
        right=m-1;
        bottom=n-1;
        left=0;
        while(top<=bottom && left<=right)
{
    for(int i=left;i<=right;i++){
        v.push_back(matrix[top][i]);
       
    }
    top++;
    
    for(int i=top;i<=bottom;i++){
        v.push_back(matrix[i][right]);
    }
    right--;
 if(top<=bottom){
    for(int i=right;i>=left;i--){
        v.push_back(matrix[bottom][i]);

    }
    bottom--;}
      if(left<=right) {
    for(int i=bottom;i>=top;i--){
        v.push_back(matrix[i][left]);
    }
    left++;}
}    return v;
}

};
```
<!--in this question we are using for loop to move circular and a while loop to continue while not end-->