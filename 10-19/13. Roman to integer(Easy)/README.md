# 罗马数字转换成阿拉伯数字
#### *Roman to integer*

* Given a roman numeral, convert it to an integer.

* Input is guaranteed to be within the range from 1 to 3999.

**example 1**
```
input: CCCLXXXIX
output: 389

```

### 思路
1. dict存储单个罗马字母代表的阿拉伯数字
2. 初始状态`sum = 0`，循环遍历字符串，如果 `s[i]`所代表的阿拉伯数字大于`s[i+1]`的，则加到`sum`上，如果小于，则`sum`减去`s[i]`代表的阿拉伯数字



### 代码
```
class Solution(object):
    def romanToInt(self, s):
        """
        :type s: str
        :rtype: int
        """
        a = {'M': 1000, 'D': 500, 'C': 100, 'L': 50, 'X': 10, 'V': 5, 'I': 1}
        sum = 0
        for i in range(len(s) - 1): #range右边界len(s) - 1 保证 i + 1不会下标越界
            if a[s[i]] < a[s[i+1]]:
                sum -= a[s[i]]
            else:
                sum += a[s[i]]
        return sum + a[s[len(s) - 1]]
```