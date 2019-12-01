给定一个字符串 s，你可以通过在字符串前面添加字符将其转换为回文串。找到并返回可以用这种方式转换的最短回文串。

示例 1:

输入: "aacecaaa"
输出: "aaacecaaa"
示例 2:

输入: "abcd"
输出: "dcbabcd"



```c++
class Solution {

public:

    string shortestPalindrome(string s) {

        int n = s.size();

        string r = s;

        reverse(r.begin(), r.end());

        string str = s + "#" + r;

        vector<int> next(2 * n + 2);

        getNext(str, next);

        return r.substr(0, n - next[2 * n + 1]) + s;

    }

    void getNext(string& str, vector<int>& next) {

        next[0] = -1;

        int i = 0, j = -1;

        while (i < str.size()) {

            if (j == -1 || str[i] == str[j]) {

                next[++i] = ++j;

            }

            else j = next[j];

        }

    }

};
```

