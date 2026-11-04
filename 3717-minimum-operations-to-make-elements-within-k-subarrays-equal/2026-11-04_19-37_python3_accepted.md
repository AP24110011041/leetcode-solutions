# 3717. Minimum Operations to Make Elements Within K Subarrays Equal
  
<br>**Problem:** https://leetcode.com/problems/minimum-operations-to-make-elements-within-k-subarrays-equal/<br>

**Difficulty:** Hard<br>
**Topics:** Array, Hash Table, Math, Dynamic Programming, Sliding Window, Heap (Priority Queue)<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-11-04 19:37 local time

**Runtime:** 3158 ms (beats 80.76899999999995%)
**Memory:** 39.6 MB (beats 82.6922%)


<!-- leetgit:submissionId=2189389822 codeHash=fcc357287323fb93c5e3eaf10a13afad1d51fbbc8319e7ef8046e211f7510a09 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Window:
    """A sorted window that keeps the sum of its h = x // 2 smallest values."""

    def __init__(self, values):
        self.h, self.odd = len(values) // 2, len(values) & 1
        self.sorted = SortedList(values)
        self.low, self.total = sum(self.sorted[:self.h]), sum(values)

    @property
    def cost(self):  # larger half minus smaller half
        return self.total - 2 * self.low - self.odd * self.sorted[self.h]

    def slide(self, out, new):
        s, h = self.sorted, self.h
        if new < s[h - 1]:  # new joins the h smallest and pushes their largest up
            self.low += new - s[h - 1]
        s.add(new)
        if out <= s[h - 1]:  # out was among the h smallest: the next value moves down
            self.low += s[h] - out
        s.remove(out)
        self.total += new - out
        return self.cost


class Solution:
    def minOperations(self, nums: List[int], x: int, k: int) -> int:
        win = Window(nums[:x])
        cost = [win.cost] + [win.slide(out, new) for out, new in zip(nums, nums[x:])]
        best = [0] * (len(nums) + 1)  # best[i]: min ops for the windows placed so far inside nums[:i]
        for _ in range(k):
            best = list(accumulate([inf] * x + [b + c for b, c in zip(best, cost)], min))
        return best[-1]
```
