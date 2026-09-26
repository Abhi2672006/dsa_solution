# Solution
```cpp
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        if(root==nullptr) return {};
        vector<vector<int>> arr;
        vector<int> arr1;
        queue<TreeNode*> q;
        q.push(root);
        int level;
        arr.push_back({root->val});
    
        while(!q.empty()){
            level=q.size();
            for(int i=0;i<level;i++){
                TreeNode* node=q.front();
                q.pop();
                if(node->left){
                    arr1.push_back(node->left->val);
                    q.push(node->left);
                }
                if(node->right){
                    arr1.push_back(node->right->val);
                    q.push(node->right);
                }
            }
            if(arr1.size()>0) arr.push_back(arr1);
            
            arr1.clear();
        }
        return arr;
        
    }
};
```
## Complexity 
- **Time:**O(n)
- **Space:**O(n)