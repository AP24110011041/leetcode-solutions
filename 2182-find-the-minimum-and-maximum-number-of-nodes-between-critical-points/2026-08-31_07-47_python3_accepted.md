# 2182. Find the Minimum and Maximum Number of Nodes Between Critical Points
  
<br>**Problem:** https://leetcode.com/problems/find-the-minimum-and-maximum-number-of-nodes-between-critical-points/<br>

**Difficulty:** Medium<br>
**Topics:** Linked List<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-08-31 07:47 local time

**Runtime:** 106 ms (beats 16.876800000000003%)
**Memory:** 62.1 MB (beats 99.2443%)


<!-- leetgit:submissionId=2125585832 codeHash=aab6e19d0b08696f9d4842fff6443e9046f61227c12bbeee6772ded71729b89c notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def nodesBetweenCriticalPoints(self, head):
        nums = []

        while head:
            nums.append(head.val)
            head = head.next

        criticalPoints = []

        n = len(nums)

        for i in range(1, n - 1):
            if nums[i] > nums[i - 1] and nums[i] > nums[i + 1]:
                criticalPoints.append(i)
            elif nums[i] < nums[i - 1] and nums[i] < nums[i + 1]:
                criticalPoints.append(i)

        m = len(criticalPoints)

        if m < 2:
            return [-1, -1]

        minDist = float('inf')

        maxDist = criticalPoints[m - 1] - criticalPoints[0]

        for i in range(1, m):
            minDist = min(
                minDist,
                criticalPoints[i] - criticalPoints[i - 1]
            )

        return [minDist, maxDist]
```
