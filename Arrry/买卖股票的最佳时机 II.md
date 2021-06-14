<https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-ii/>

## 买卖股票问题系列中的第二个问题，贪心+DP；

# 题目概述：
一看题目就可以采用DP做，但是第一次看到DP可以这样做；

## DP：
DP问题第一次见到双转移方程DP；
DP的条件在于，在第i天到底卖不卖；
对于有没有股票有两种情况，每种情况又有两种情况：
dp\[i][0]代表手里没有股票的收益；
### 如果第i天没股票：
#### 1. 第i-1天也没有股票买入；
#### 2.第i-1天有股票，但是卖出；
### 如果第i天有股票；
#### 1.第i-1天就有股票；
#### 2.第i-1天没有股票，在第i天买入；

所以最后的状态转移方程可以为：

![image-20210614020001343](C:\Users\Innovation\AppData\Roaming\Typora\typora-user-images\image-20210614020001343.png)

值得注意的是自己写的时候有三个问题：
1.这个状态转移方程中收益针对的是prices[i]，买入亏prices[i]，卖出直接赚prices[i]；
2.乍一看可能-prices[i]的方式可能会产生问题，但是考虑如果是升序，必定会出现prices[i]+(-prices[i])大于零的收益情况；
3.最后手里卖出股票肯定比砸手里好，因此最后的值为dp\[n-1][0]

## 贪心：
用贪心算法也可以，自己当时没想到；
其实这个问题相当于变相求一个序列中的若干个升序连续子序列，贪心一次遍历即可，自己当时没想到；

并且求子序列的方法也很取巧；
由于并没有要求全部求出子序列，只需要求差值和，所以可以使用升序序列中的nums[i]-nums[i-1]来连续求和，这样可以减少复杂度；
即：1，2，3，4，5的插值和即位5-1=(2-1)+(3-2)+(4-3)+(5-4)；

# 具体代码：
## DP：
```C++
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int n = prices.size();
        vector<vector<int>>dp(n,vector<int>(2));
        dp[0][0] = 0;
        dp[0][1] = -prices[0];
        for (int i = 1; i < n; i++) {
            dp[i][0] = max(dp[i - 1][0], dp[i - 1][1] + prices[i]);
            dp[i][1] = max(dp[i - 1][1], dp[i-1][0] - prices[i]);
        }
        return dp[n - 1][0];
    }
};
```

## 贪心算法：

```C++
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int cnt = 0;
        for (int i = 1; i < prices.size(); i++) {
            cnt += max(0, prices[i] - prices[i - 1]);
        }
        return cnt;
    }
};
```
