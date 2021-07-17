<https://leetcode-cn.com/problems/kth-smallest-element-in-a-bst/>

## 中等题，利用排序树中序递增性质；

# 题目概述：

利用的是排序树中序递增性质，ezsy；


# 具体代码：
```C++
void inorder(TreeNode* root, int& num, int k,int& ret) {
	if (root == NULL)
		return;
	inorder(root->left,num,k,ret);
	num++;
	if (num == k) {
		ret = root->val;
	}
	inorder(root->right,num,k,ret);
}


int kthSmallest(TreeNode* root, int k) {
	int num = 0, ret = -1;
	inorder(root, num, k, ret);
	return ret;
}

```