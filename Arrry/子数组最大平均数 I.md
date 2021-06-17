<https://leetcode-cn.com/problems/maximum-average-subarray-i/>

## 滑动窗口，连续和问题；

# 题目概述：
滑动窗口，维持一个滑动窗口，左端吐出，右端并入；
每次记录最大的值；

# 具体代码：
```C++
class Solution {
public:
    double findMaxAverage(vector<int>& nums, int k) {
        int maxn = 0;
        int sum = 0;
        for (int i = 0; i < k; i++) {
            sum += nums[i];
        }
        maxn = sum;
        for (int i = 1; i + k - 1 < nums.size(); i++) {
            sum += nums[i + k - 1] - nums[i-1];
            maxn = max(maxn, sum);
        }
        return double(maxn)/k;
    }
};
```
