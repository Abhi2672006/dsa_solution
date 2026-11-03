# Solution
```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    int step=0;
    int dfs(TreeNode* root){
        if(root==NULL) return 0;
        int left_height=dfs(root->left); //height of the left subtree 
        int right_height=dfs(root->right); //height of the right subtree
        step=max(step,left_height+right_height); 
        return 1+max(left_height,right_height);
    }
    int diameterOfBinaryTree(TreeNode* root) {
        if(root==NULL) return 0;
       dfs(root);
         return step;

      
    }
};
```