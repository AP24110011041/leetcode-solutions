# 1487. Cinema Seat Allocation
  
<br>**Problem:** https://leetcode.com/problems/cinema-seat-allocation/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Hash Table, Greedy, Bit Manipulation<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-08-20 19:44 local time

**Runtime:** 35 ms (beats 68.71810000000004%)
**Memory:** 23 MB (beats 53.07690000000001%)


<!-- leetgit:submissionId=2114017888 codeHash=656137f739a66ec380c95773c062e020291e4603e3b697290ce3e18e16b63065 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
  def maxNumberOfFamilies(self, n, reservedSeats):
    # Create a dictionary of sets to store the reserved seats by row
    seats = collections.defaultdict(set)
    # Iterate through the reserved seats
    for i,j in reservedSeats:
      # If the seat is an outside seat in the row, add it to tallies 0 and 1
      if j in {4,5}: 
        seats[i].add(0) 
        seats[i].add(1)
      # If the seat is a middle seat in the row, add it to tallies 1 and 2
      elif j in {6,7}: 
        seats[i].add(1)
        seats[i].add(2)
      # If the seat is another type of seat, add it to the corresponding tally
      elif j in {8,9}: 
        seats[i].add(2)
      elif j in {2,3}:
        seats[i].add(0)
      # Initialize the result to twice the number of rows
      res = 2*n
    # Iterate through the rows of seats
    for i in seats:
      # If a row has all three tallies, subtract two from the result
      if len(seats[i]) == 3: res -= 2
      # Otherwise, subtract one from the result
      else: res -= 1

    # Return the final result
    return res
```
