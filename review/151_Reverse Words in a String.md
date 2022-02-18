## 题目
https://leetcode-cn.com/problems/reverse-words-in-a-string/

## 思路
imitation

## python3
```python3
class Solution:
    def reverseWords(self, s: str) -> str:
        def trim_(s):
            left, right = 0, len(s) - 1
            while left <= right and s[left] == ' ':
                left += 1
            while right <= right and s[right] == ' ':
                right -= 1
            
            output = []
            while left <= right:
                if s[left] != ' ':
                    output.append(s[left])
                # 细节！！！
                # s[left] == ' '
                # 当output中最后一个字符不为空时候加入空格，如果有就不加入
                elif output[-1] != ' ':
                    output.append(s[left])
                left += 1

            return output

        def reverse(l, left, right):
            while left <= right:
                l[left], l[right] = l[right], l[left]
                left += 1
                right -= 1
        
        def reverse_each_words(l):
            n = len(l)
            start = end = 0
            while end < n:
                # 循环至单词的末尾
                while end < n and l[end] != ' ':
                    end += 1
                # 翻转单词
                reverse(l, start, end - 1)
                # 更新start，去找下一个单词
                start = end + 1
                end += 1

        l = trim_(s)
        reverse(l, 0, len(l) - 1)
        reverse_each_words(l)

        return ''.join(l)

```

## 复杂度分析
* time n
* space n

## 相关题目
1. 待补充