# Solution
**Topic:**Recursion
```cpp
class Solution{
public:
    int preq=0;
    TreeNode* build(vector<int>& preorder,int left,int right,unordered_map<int,int>& mp){
    if(left>right) return NULL;
    int val=preorder[preq++];
    TreeNode* node=new TreeNode(val);
    int mid=inorder[val];
    root->left=build(preorder,left,mid-1);
    root->right=build(preorder,mid+1,right);
    return root;
    }

    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
        unordered_map<int,int> mp;
        for(int i=0;i<inorder.size();i++){
            mp[inorder[i]]=i;
        }
        return build(preorder,0,(int)inorder.size()-1,mp);
    }

};
```
# Complexity
**Time:**O(n)
**Space:**O(n)