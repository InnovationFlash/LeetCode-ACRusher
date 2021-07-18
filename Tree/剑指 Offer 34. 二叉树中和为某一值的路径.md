<https://leetcode-cn.com/problems/er-cha-shu-zhong-he-wei-mou-yi-zhi-de-lu-jing-lcof/>

## 中等题，回溯+DFS

# 题目概述：

没啥可说的；


# 具体代码：
```C++
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
    void dfs(vector<vector<int>>& res, vector<int>& path, TreeNode* root,int sam,int target) {
        if (root == NULL)
            return;
        path.push_back(root->val);
        if (sam + root->val == target && root->left == NULL && root->right == NULL) {
            res.push_back(path);
        }
        dfs(res, path, root->left, sam + root->val, target);
        dfs(res, path, root->right, sam + root->val, target);
        path.pop_back();
    }

    vector<vector<int>> pathSum(TreeNode* root, int target) {
        vector<vector<int>>res;
        vector<int>path;
        dfs(res, path, root, 0, target);
        return res;
    }
};
```