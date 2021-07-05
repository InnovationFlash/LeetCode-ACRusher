<https://leetcode-cn.com/problems/implement-strstr/>

## 简单题，字符串匹配，未用KMP算法；

# 题目概述：
直接暴力，还用不到KMP，后续可以不全有一下；
# 具体代码：

```C++
class Solution {
public:
    bool charge(const string& s1, const string& s2, int a){
        for (int j = 0; j < s2.size(); j++) {
            if (s2[j] != s1[a + j])
                return false;
        }
        return true;
    }

    int strStr(string haystack, string needle) {
        if (needle.size() == 0)
            return 0;
        if (haystack.size() == 0||haystack.size()<needle.size())
            return -1;
        for (int i = 0; i < haystack.size() - needle.size()+1; i++) {
            if (haystack[i] == needle[0]&&charge(haystack,needle,i)){
                return i;
            }
        }
        return -1;
    }
};
```