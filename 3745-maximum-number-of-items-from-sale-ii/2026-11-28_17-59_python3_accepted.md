# 3745. Maximum Number of Items From Sale II
  
<br>**Problem:** https://leetcode.com/problems/maximum-number-of-items-from-sale-ii/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Greedy, Sorting, Heap (Priority Queue)<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-11-28 17:59 local time

**Runtime:** 283 ms (beats 54.05410000000006%)
**Memory:** 59.8 MB (beats 24.324400000000004%)


<!-- leetgit:submissionId=2205125825 codeHash=8c8467c1965a9852c133aec96252cea1a9424bc26c617c14b85e055e99286108 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def maximumSaleItems(self, items: List[List[int]], budget: int) -> int:
        factors, prices = zip(*items)
        have = [0] * (len(items) + 1)  # have[f]: items with factor f
        for factor in factors:
            have[factor] += 1
        deals = cache(lambda factor: sum(have[factor::factor]) - 1)  # counted when an item is reached

        cheapest = min(prices)
        heap = [(price, factor) for factor, price in items if price < 2 * cheapest]
        heapify(heap)
        copies = 0
        while heap and heap[0][0] <= budget:  # the cheapest deal left is affordable
            price, factor = heappop(heap)
            pairs = min(deals(factor), budget // price)
            copies += 2 * pairs
            budget -= pairs * price
        return copies + budget // cheapest
```
