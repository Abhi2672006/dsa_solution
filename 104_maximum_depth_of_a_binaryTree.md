# Solution bfs
```cpp
class Solution {
public:
    int maxDepth(TreeNode* root) {
        if(root==NULL) return 0;
        queue<TreeNode*> q;
        q.push(root);
        int level;
        int count=0;
        while(!q.empty()){
            level=q.size();
            
            for(int i=0;i<level;i++){
                TreeNode* node=q.front();
                q.pop();
                if(node->left) q.push(node->left);
                if(node->right) q.push(node->right);
            }
            count++;

        }
        return count;
    }
};
```
## Complexity
- **Time:**O(n)
- **Space:**O(n)

# Solution dfs
```cpp
class Solution {
public:
   int counti(TreeNode* node,int count){
    if(node==NULL) return count;
    count=max(counti(node->left,count+1),counti(node->right,count+1));
    
    return count;
   }

    
    int maxDepth(TreeNode* root) {

       
        return counti(root,0);
    }
};
```
## Complexity
- **Time:**O(n)
- **Space:**O(n) recursion stack
