# 4257. Sum of Sortable Integers
  
<br>**Problem:** https://leetcode.com/problems/sum-of-sortable-integers/<br>

**Difficulty:** Hard<br>
**Topics:** Array, Math, Sorting, Enumeration<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-20 12:43 local time

**Runtime:** 3835 ms (beats 12.087999999999965%)
**Memory:** 33.6 MB (beats 28.571499999999972%)


<!-- leetgit:submissionId=2176846119 codeHash=17245313b37c9ddd31f36dcdb1317d51b285cace471ec82a3394517dba4ff182 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def operation(self, k, nums):
        n = len(nums)
        chunks = n // k
        minMax = []

        for i in range(chunks):
            start = i * k
            mini = float('inf')
            maxi = float('-inf')
            cnt = 0

            for j in range(k):
                curr = nums[start + j]
                next_val = nums[start + (j + 1) % k]

                mini = min(mini, curr)
                maxi = max(maxi, curr)

                if curr > next_val:
                    cnt += 1

            if cnt > 1:
                return False

            minMax.append((mini, maxi))

        for i in range(chunks - 1):
            if minMax[i][1] > minMax[i + 1][0]:
                return False

        return True

    def sortableIntegers(self, nums):
        n = len(nums)
        ans = 0

        i = 1
        while i * i <= n:
            if n % i == 0:
                if self.operation(i, nums):
                    ans += i

                if i != n // i:
                    if self.operation(n // i, nums):
                        ans += (n // i)
            i += 1

        return ans
```
