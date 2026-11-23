# 1477. Product of the Last K Numbers
  
<br>**Problem:** https://leetcode.com/problems/product-of-the-last-k-numbers/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Math, Design, Data Stream, Prefix Sum<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-11-23 20:18 local time

**Runtime:** 151 ms (beats 17.70930000000012%)
**Memory:** 33.7 MB (beats 44.16670000000001%)


<!-- leetgit:submissionId=2201984878 codeHash=f629f355a5e28394317183ab4918cd628b6bf7945240ced54c4a1dc527a3ca64 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class ProductOfNumbers:

    def __init__(self):
        self.prefix = [1]  # prefix[i]: the product of the first i numbers after the last zero

    def add(self, num: int) -> None:
        if num == 0:
            self.prefix = [1]  # a window that reaches this zero is 0, so forget everything before it
        else:
            self.prefix.append(self.prefix[-1] * num)

    def getProduct(self, k: int) -> int:
        if k >= len(self.prefix):  # the window reaches back to a zero
            return 0
        return self.prefix[-1] // self.prefix[-1 - k]
```
