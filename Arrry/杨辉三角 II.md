<https://leetcode-cn.com/problems/pascals-triangle-ii/>

## 杨辉三角一维数组进阶版；

# 题目概述：
之前是设一个二维数组整体迭代；
但是使用一维数组也可以做；

直接逐行从后向前遍历；
之所以从后向前遍历是因为当新的一行最后一个为1的时候，其核心元素恰好在上一层的位置；
如果采用从前向后遍历，则会是后续元素失去上一行的值，因此应该：
ret[j]=ret[j]+ret[j-1];
从后向前，而不是从前向后；

# 具体代码：
```C++
#include<iostream>
#include<stdlib.h>
#include<vector>
#include<map>
#include<string>
#include<algorithm>
using namespace std;

vector<int> getRow(int rowIndex) {
	vector<int>ret(rowIndex + 1);
	ret[0] = 1;
	for (int i = 0; i <= rowIndex; i++) {
		ret[i] = 1;
		for (int j = i-1; j >= 1; j--) {
			ret[j] = ret[j] + ret[j - 1];
		}
	}
	return ret;
}

int main() {
	return 0;
}
```
