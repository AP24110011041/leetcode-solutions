# 2347. Count Nodes Equal to Average of Subtree
  
<br>**Problem:** https://leetcode.com/problems/count-nodes-equal-to-average-of-subtree/<br>

**Difficulty:** Medium<br>
**Topics:** Tree, Depth-First Search, Binary Tree<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-10 20:08 local time

**Runtime:** 56 ms (beats 30.353699999999982%)
**Memory:** 19.6 MB (beats 69.4601%)


<!-- leetgit:submissionId=2137591246 codeHash=1c7ba0e13b0878057480969bcf296e314b4323677dc8aff86fa0ad4819e4a196 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def averageOfSubtree(self, root):
        self.count = 0

        def trav(node):
            if node is None:
                return (0, 0)

            leftSum, leftCount = trav(node.left)
            rightSum, rightCount = trav(node.right)

            subtreeSum = leftSum + rightSum + node.val
            subtreeCount = leftCount + rightCount + 1

            if subtreeSum // subtreeCount == node.val:
                self.count += 1

            return (subtreeSum, subtreeCount)

        trav(root)
        return self.count
```
