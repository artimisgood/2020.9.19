# 2020.9.19 z字形变换
## 题目
将一个给定字符串根据给定的行数，以从上往下、从左到右进行 Z 字形排列。

比如输入字符串为 "LEETCODEISHIRING" 行数为 3 时，排列如下：
```java
L   C   I   R
E T O E S I I G
E   D   H   N
```
之后，你的输出需要从左往右逐行读取，产生出一个新的字符串，比如："LCIRETOESIIGEDHN"。

请你实现这个将字符串进行指定行数变换的函数：

    string convert(string s, int numRows);
    示例 1:

    输入: s = "LEETCODEISHIRING", numRows = 3
    输出: "LCIRETOESIIGEDHN"
    示例 2:

    输入: s = "LEETCODEISHIRING", numRows = 4
    输出: "LDREOEIIECIHNTSG"
    解释:
```java
L     D     R
E   O E   I I
E C   I H   N
T     S     G
```

## 解题
### 语言
c++
### 思路
通过从左向右迭代字符串，我们可以轻松地确定字符位于 Z 字形图案中的哪一行。
### 代码
```java
lass Solution {
public:
    string convert(string s, int numRows) {
        
        if(numRows==1) return s;

        vector<string> rows(min(numRows,int(s.size())));//设定一个字符串的数组，这个数组长度为*和*的最小值
        int curRow = 0;//设定现在所在字符串的位置
        bool goingDown = false;//设定要不要转换方向

        for(char c:s){
            rows[curRow] += c;//在数组的第一字符串中先插入一个字符
            if(curRow==0||curRow == numRows-1) goingDown=!goingDown;//判断是否要转换方向
            curRow += goingDown? 1:-1;//如果需要就到相邻的字符串中
        }

        string ret;
        for(string row:rows) ret += row;
        return ret;
    }
};
```
解题思路具体看：
[https://leetcode-cn.com/problems/zigzag-conversion/solution/z-zi-xing-bian-huan-by-leetcode/](https://leetcode-cn.com/problems/zigzag-conversion/solution/z-zi-xing-bian-huan-by-leetcode/)
