<https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-ii-lcof/>

## 简单题，傻吊层序遍历

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
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        vector<vector<int>>res;
        queue<TreeNode*>q;
        if (!root)
            return res;
        q.push(root);
        while (!q.empty()) {
            vector<int>vec;
            for (int i = 0, len = q.size(); i < len; i++) {
                TreeNode* t = q.front();
                q.pop();
                vec.push_back(t->val);
                if (t->left)
                    q.push(t->left);
                if (t->right)
                    q.push(t->right);
            }
            res.push_back(vec);
        }
        return res;
    }
};
```