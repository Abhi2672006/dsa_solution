# Solution 
```cpp
class Solution {
public:
    void isValid(vector<int>& v,TreeNode* root){
        if(root==nullptr) return;

        isValid(v,root->left);
        v.push_back(root->val);
        isValid(v,root->right);
    }
    bool isValidBST(TreeNode* root) {
        vector<int> v;
        isValid(v,root);

        for(int i=v.size()-1;i>0;i--){
            if(v[i-1]>=v[i]) return false;
        }
        return true;
    }
};
```
<!--Inorder Traversal of a complete binary search tree gives numbers in ascending order and we just have to check that order if not correct then not bst if yes then bst-->
## complexity
- **Time:**O(n)
- **Space:**O(n);

# Solution two
```cpp
class Solution {
public:
TreeNode* prev=NULL;
    bool isValidBST(TreeNode* root) {
        if(root==NULL) return true;

        if(!isValidBST(root->left)) return false;
        if(prev!=NULL && prev->val>=root->val) return false;
        prev=root;
        return isValidBST(root->right);
    }
};
```
## Complexity
- **Time:**O(n)
- **Space:**O(h) recursion stack