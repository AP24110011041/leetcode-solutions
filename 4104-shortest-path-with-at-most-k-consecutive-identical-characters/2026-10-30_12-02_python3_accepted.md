# 4104. Shortest Path With At Most K Consecutive Identical Characters
  
<br>**Problem:** https://leetcode.com/problems/shortest-path-with-at-most-k-consecutive-identical-characters/<br>

**Difficulty:** Medium<br>
**Topics:** String, Graph Theory, Heap (Priority Queue), Shortest Path<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-30 12:02 local time

**Runtime:** 127 ms (beats 97.59039999999999%)
**Memory:** 47.1 MB (beats 98.7952%)


<!-- leetgit:submissionId=2185287760 codeHash=402793cc63f75467cece9ac1d968e8e9d6f1863c64fa7eedb901beab85550709 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def shortestPath(self, n: int, edges: List[List[int]], labels: str, k: int) -> int:
        graph = [[] for _ in range(n)]
        for u, v, w in edges:
            graph[u].append((v, w))

        best = [k + 1] * n  # best[x]: the shortest run x was settled with, k + 1 until then
        heap = [(0, 1, 0)]  # (distance, run, node): the walk ends with run nodes labeled labels[node]
        while heap:
            d, run, x = heappop(heap)
            if run >= best[x]:  # x was settled before, no farther away and with a run no longer
                continue
            if x == n - 1:
                return d
            best[x] = run
            for y, w in graph[x]:
                r = run + 1 if labels[y] == labels[x] else 1
                if r < best[y]:
                    heappush(heap, (d + w, r, y))
        return -1
```
