<https://leetcode-cn.com/problems/lian-xu-zi-shu-zu-de-zui-da-he-lcof/>

## 动态规划/最大连续子序列和；

# 题目概述：
最长连续子序列和问题

# 具体代码：
```C++
class Solution {
public:
    bool divisorGame(int n) {
        if (n <= 1)
            return false;
        vector<bool>dp(n+1,false);
        dp[0] = dp[1] = false;
        dp[2] = true;
        for (int i = 3; i <= n; i++) {
            for (int j = 1; j < i; j++) {
                if (i % j == 0 && dp[j])
                    dp[i] = true;
            }
        }
        return dp[n];
    }
};
```