# 3375. Kth Smallest Amount With Single Denomination Combination
  
<br>**Problem:** https://leetcode.com/problems/kth-smallest-amount-with-single-denomination-combination/<br>

**Difficulty:** Hard<br>
**Topics:** Array, Math, Binary Search, Bit Manipulation, Combinatorics, Number Theory<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-08-21 19:16 local time

**Runtime:** 90 ms (beats 59.75630000000001%)
**Memory:** 19.4 MB (beats 93.9025%)


<!-- leetgit:submissionId=2115101211 codeHash=72498ff458a4d9e2d5b59640261601d4b6547a6368acbf81169934059ecb03af notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def findKthSmallest(self, coins: list[int], k: int) -> int:
        coins.sort()
        A = []
        for c in coins:
            if all(c % x for x in A):
                A.append(c)

        n = len(A)

        def check(mid):
            tot = 0
            for i in range(1, n + 1):
                q = (1 << i) - 1
                lim = 1 << n
                sgn = ((i & 1) << 1) - 1

                while q < lim:
                    x = 1
                    for j in range(n):
                        if (q >> j) & 1:
                            x = lcm(x, A[j])

                    tot += (mid // x) * sgn

                    c = q & -q
                    r = q + c
                    q = (((r ^ q) >> 2) // c) | r
            return tot >= k

        return bisect_left(range(A[0] * k + 1), True, lo=k, key=check)

```
