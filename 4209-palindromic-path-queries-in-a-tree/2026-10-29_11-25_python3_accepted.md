# 4209. Palindromic Path Queries in a Tree
  
<br>**Problem:** https://leetcode.com/problems/palindromic-path-queries-in-a-tree/<br>

**Difficulty:** Hard<br>
**Topics:** Array, String, Divide and Conquer, Bit Manipulation, Tree, Depth-First Search, Binary Indexed Tree, Segment Tree<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-29 11:25 local time

**Runtime:** 674 ms (beats 93.87759999999999%)
**Memory:** 51.5 MB (beats 89.79599999999998%)


<!-- leetgit:submissionId=2184468524 codeHash=3d711c157bad07200bf991144aa9fdeeb14871bd58e1f5810ac13fa421782daa notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Tree:  # Euler tour: the subtree of x is tin[x] .. tout[x] - 1; LCA by a sparse table over the DFS order
    def __init__(self, n: int, edges: list[list[int]]):
        graph = [[] for _ in range(n)]
        for u, v in edges:
            graph[u].append(v)
            graph[v].append(u)

        parent, tin, tout, order = [0] * n, [0] * n, [0] * n, []  # the root is its own parent; order: the nodes in DFS order
        stack = [0]
        while stack:  # DFS without recursion; ~x marks the moment x's subtree is done
            x = stack.pop()
            if x < 0:
                tout[~x] = len(order)
                continue
            tin[x] = len(order)
            order.append(x)
            stack.append(~x)
            for y in graph[x]:
                if y != parent[x]:
                    parent[y] = x
                    stack.append(y)

        first = [[tin[parent[x]] for x in order]]  # first[k][i]: the earliest parent among order[i : i + 2^k]
        for k in range(1, n.bit_length()):
            prev = first[-1]
            first.append([*map(min, prev, prev[1 << k - 1:])])
        self.parent, self.tin, self.tout, self.order, self.first = parent, tin, tout, order, first

    def lca(self, u: int, v: int) -> int:  # the parent that comes first in DFS order among the nodes after u up to v
        if u == v:
            return u
        l, r = sorted((self.tin[u], self.tin[v]))
        k = (r - l).bit_length() - 1
        return self.order[min(self.first[k][l + 1], self.first[k][r - (1 << k) + 1])]


class RootPaths:  # paths[x]: XOR of the letter bits from the root down to x
    def __init__(self, tree: Tree, bit: list[int]):
        self.start = start = bit[:]  # the masks for the initial letters: a parent comes before its children in DFS order
        for x in tree.order[1:]:
            start[x] ^= start[tree.parent[x]]
        self.tin, self.tout = tree.tin, tree.tout
        self.fenwick = [0] * (len(bit) + 1)  # a Fenwick tree over the Euler tour with the changes since the start

    def flip(self, x: int, d: int):  # XOR d into the root path of every node in x's subtree
        fenwick = self.fenwick
        for i in self.tin[x] + 1, self.tout[x] + 1:  # d starts at x's subtree and cancels out after it
            while i < len(fenwick):
                fenwick[i] ^= d
                i += i & -i

    def __getitem__(self, x: int) -> int:
        fenwick, mask, i = self.fenwick, self.start[x], self.tin[x] + 1
        while i:
            mask ^= fenwick[i]
            i -= i & -i
        return mask


class Solution:
    def palindromePath(self, n: int, edges: list[list[int]], s: str, queries: list[str]) -> list[bool]:
        tree = Tree(n, edges)
        bit = [1 << ord(c) - 97 for c in s]  # bit[x]: the bit of x's letter
        paths = RootPaths(tree, bit)

        ans = []
        for q in queries:
            kind, a, b = q.split()
            if kind == 'update':
                x, new_bit = int(a), 1 << ord(b) - 97
                paths.flip(x, bit[x] ^ new_bit)  # the new letter changes the root path of every node in x's subtree
                bit[x] = new_bit
            else:
                u, v = int(a), int(b)
                mask = paths[u] ^ paths[v] ^ bit[tree.lca(u, v)]  # the LCA cancels out in paths[u] ^ paths[v], so add it back
                ans.append(mask.bit_count() <= 1)  # at most one letter is odd
        return ans
```
