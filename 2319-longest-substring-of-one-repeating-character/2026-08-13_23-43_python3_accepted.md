# 2319. Longest Substring of One Repeating Character
  
<br>**Problem:** https://leetcode.com/problems/longest-substring-of-one-repeating-character/<br>

**Difficulty:** Hard<br>
**Topics:** Array, String, Segment Tree, Ordered Set<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-08-13 23:43 local time

**Runtime:** 3130 ms (beats 49.18169999999989%)
**Memory:** 105.2 MB (beats 29.50949999999996%)


<!-- leetgit:submissionId=2105825512 codeHash=2c1792bd287a8815efcb999a8a7a231965dfdfcde4ddf3190298c832be70ca0d notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def longestRepeating(self, s: str, queryCharacters: str, queryIndices: List[int]) -> List[int]:
        n = len(s)
        tree = [None] * (4 * n)
        def merge(left, right):
            if left is None:
                return right
            if right is None:
                return left
            lc, lrc, llen, lp, ls, lb = left
            rlc, rc, rlen, rp, rs, rb = right
            length = llen + rlen

            prefix = lp

            if lrc == rlc and lp == llen:
                prefix = llen + rp

            suffix = rs

            if lrc == rlc and rs == rlen:
                suffix = rlen + ls

            best = max(lb, rb)

            if lrc == rlc:
                best = max(best, ls + rp)

            return [lc, rc, length, prefix, suffix, best]

        def build(node, start, end):
            if start == end:
                tree[node] = [s[start], s[start], 1, 1, 1, 1]
                return

            mid = (start + end) // 2

            build(node * 2, start, mid)
            build(node * 2 + 1, mid + 1, end)

            tree[node] = merge(tree[node * 2], tree[node * 2 + 1])

        def update(node, start, end, index, char):
            if start == end:
                tree[node] = [char, char, 1, 1, 1, 1]
                return

            mid = (start + end) // 2

            if index <= mid:
                update(node * 2, start, mid, index, char)
            else:
                update(node * 2 + 1, mid + 1, end, index, char)

            tree[node] = merge(tree[node * 2], tree[node * 2 + 1])

        build(1, 0, n - 1)

        answer = []

        for char, index in zip(queryCharacters, queryIndices):
            update(1, 0, n - 1, index, char)
            answer.append(tree[1][5])

        return answer
```
