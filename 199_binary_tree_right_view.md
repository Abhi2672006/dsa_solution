# Solution bfs queue
```cpp

class Solution {
public:
    vector<int> rightSideView(TreeNode* root) {
        if(root==NULL) return {};
        queue<TreeNode*> q;
        q.push(root);
        vector<int> v;
      
        int k;
        while(!q.empty()){
        
             int level=q.size();
           
            for(int i=0;i<level;i++){
                TreeNode* node=q.front();
                q.pop();
            
            if(node->left){
                
                q.push(node->left);
            }
            if(node->right){
                 
                q.push(node->right);
            }
            if(i==level-1) v.push_back(node->val);
        }}
        return v;
    }
};
```
## Complexity
**Topic:**bfs queue
**Time:** O(n)
**Space:**O(n) //queue

# Solution two dfs
```cpp
class Solution {
public:
    vector<int> v;
    void dfs(TreeNode* root,int depth){
        if(!root) return;
        if(depth==v.size()) v.push_back(root->val);
        dfs(root->right,depth+1);
        dfs(root->left,depth+1);
        
    }
    vector<int> rightSideView(TreeNode* root) {
        dfs(root,0);
        return v;
    }
};
```
## Complexity
**Topic:**dfs
**Time:**O(n)
**Space:**O(h);