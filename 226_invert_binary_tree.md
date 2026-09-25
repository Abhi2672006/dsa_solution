# Solution recursion
```cpp
class Solution {
public:
    TreeNode* invertTree(TreeNode* root) {
        if(root==NULL) return root;

        TreeNode* left=invertTree(root->left);
        TreeNode* right=invertTree(root->right);

        root->left=right;
        root->right=left;
        return root;
    }
};
```
## Complexity
- **Time:**O(n)
- **Space:**O(n) recursion stack