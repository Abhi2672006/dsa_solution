# Solution
 ```cpp
 class Solution {
public:
    void inorder(TreeNode* root ,int k, int& count,int& ans){
        if(root==NULL || count>=k) return;
        
        inorder(root->left,k,count,ans);
        count++;
        if(count==k){
            ans=root->val;
            
            return;
        }
        inorder(root->right,k,count,ans);
        }
    int kthSmallest(TreeNode* root, int k) {
        int ans;
        int count=0;
        inorder(root,k,count,ans);
        return ans;
    }
};
```
## Complexity
- **Time:**O(n)
- **Space:**O(h) recursion stack