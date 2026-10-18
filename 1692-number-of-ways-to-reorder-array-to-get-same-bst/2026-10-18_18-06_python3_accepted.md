# 1692. Number of Ways to Reorder Array to Get Same BST
  
<br>**Problem:** https://leetcode.com/problems/number-of-ways-to-reorder-array-to-get-same-bst/<br>

**Difficulty:** Hard<br>
**Topics:** Array, Math, Divide and Conquer, Dynamic Programming, Tree, Union-Find, Binary Search Tree, Memoization, Combinatorics, Binary Tree, Fermat's Little Theorem<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-18 18:06 local time

**Runtime:** 9 ms (beats 99.3865%)
**Memory:** 19.6 MB (beats 97.54599999999999%)


<!-- leetgit:submissionId=2175378515 codeHash=e748ecacc1f25ed6457284cd7d8e54b32adba19bd68dda96e9dfaa574a68d150 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def numOfWays(self, nums: List[int]) -> int:
        n = len(nums)
        born = [-1] * (n + 2)  # insertion time of each value; the walls 0 and n + 1 come before everything
        for t, x in enumerate(nums):
            born[x] = t

        sizes, stack = 1, [0]  # product of subtree sizes; values with increasing insertion times
        for v in range(1, n + 2):
            while born[stack[-1]] > born[v]:  # v is the right wall of the value on top
                stack.pop()
                sizes *= v - stack[-1] - 1  # and the value below it is the left wall
            stack.append(v)

        return (factorial(n) // sizes - 1) % (10**9 + 7)
```
