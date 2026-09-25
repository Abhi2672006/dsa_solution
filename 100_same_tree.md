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
    void preorder(TreeNode* p,vector<int> &count){
        if(p==nullptr){
            count.push_back(10001);
            return;
        }
        count.push_back(p->val);
        preorder(p->left,count);
        preorder(p->right,count);
    }
    bool isSameTree(TreeNode* p, TreeNode* q) {
        vector<int> a;
        preorder(p,a);
        vector<int> b;
        preorder(q,b);
       if(a.size()!=b.size()) return false;
       for(int i=0;i<a.size();i++){
        if(a[i]!=b[i]) return false;
       }
       return true;

    }
};
```
## Complexity
- **Time:**o(n+m)
- **space:**O(n+m)

# Solution two recursion
```cpp
class Solution {
public:
    bool isSameTree(TreeNode* p, TreeNode* q) {
        if(p==NULL && q==NULL) return true;
        if(p==NULL || q==nullptr) return false;
        if(p->val!=q->val) return false;
        

        return isSameTree(p->left,q->left) && isSameTree(p->right,q->right);
    }
};
```
## complexity
- **Time:**O(n+m)
- **Space:**O(min(h1,h2));