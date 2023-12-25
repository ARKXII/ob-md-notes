#hashmap-array 
# summary

Given an integer array `nums`, return _an array_ `answer` _such that_ `answer[i]` _is equal to the product of all the elements of_ `nums` _except_ `nums[i]`.

The product of any prefix or suffix of `nums` is **guaranteed** to fit in a **32-bit** integer.

You must write an algorithm that runs in `O(n)` time and without using the division operation.

**Example 1:**

**Input:** nums = [1,2,3,4]
**Output:** [24,12,8,6]

**Example 2:**

**Input:** nums = [-1,1,0,-3,3]
**Output:** [0,0,9,0,0]

## thought process

- first i got the for loop working and declared what I think is needed
```python
results = []
hashMap = []

n = len(nums)

for i in range(n):

return results
```

- im trying to find a way to isolate *i* so that i'm free to do operations on the other numbers
- maybe i can use hashMap as sort of a temporary array to do operations on. i just need a way to isolate.

```python
for i in range(n):
	hashMap = [x for x in nums if x != i]
```
*the above algorithm gets all elements exept the current one but i don't think that this will be O(n) so the hunt continues.*

---

- this one is more mathematically complex to think about. after some research, the solution lies in this:

**nums**
| 1 | 2 | 3 | 4 |

- initialize an integer *prefix = 1*
- initialize an output list *output*

```python
output = [1]

for i in range(len(num)):
	output[num[i] * prefix]
```

- multiply the current element to the prefix then append it to *output*

**output**
| 1 | 1 | 2 | 6 |

- perform a reverse loop on *num* and multiply it to *output list*

```python
for i in reverse(range(len(num)):
	output[i] *= num[i]

return output[]
```