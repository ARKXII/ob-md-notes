#hashmap-array 
# summary

Given an unsorted array of integers `nums`, return _the length of the longest consecutive elements sequence._

You must write an algorithm that runs in `O(n)` time.

**Example 1:**

**Input:** nums = [100,4,200,1,3,2]
**Output:** 4
**Explanation:** The longest consecutive elements sequence is `[1, 2, 3, 4]`. Therefore its length is 4.

**Example 2:**

**Input:** nums = [0,3,7,2,5,8,4,6,0,1]
**Output:** 9

## thought process

the first step is probably to sort, but i'm not sure how to sort in O(n) time. 

---

i found this sort function that runs in O(n) time
```python
def counting_sort(arr):
    max_value = max(arr)
    counts = [0] * (max_value + 1)

    for num in arr:
        counts[num] += 1

    sorted_arr = []
    for i in range(max_value + 1):
        sorted_arr.extend([i] * counts[i])

    return sorted_arr

```

so I'll pass this into the algorithm.

---

so somehow, we need to find consecutive numbers in the array, which we can probably do by subtracting the current element to the next element, then pushing it into an output array

```python
for i in range(len(nums)):
	output = nums[i] - nums[i+1]
	if output == -1:
		sqnc++
	else
		return sqnc
```

---

## test cases

i ran into a few test case problems and subsequently, i needed to ask chatgpt for help.

```
nums = []
```

i had to write a return [] if empty string

```
nums = [0]
```

code kept returning 0 so i had to write a return 1 

by far the biggest problem was

```
nums = [-1, 0, 1, 3, 4, 5, 6, 7]
```

code kept breaking at -1, 0, 1 so i asked chatgpt for help:

```python
class Solution:
    def longestConsecutive(self, nums):
        if not nums:
            return 0
        num_set = set(nums)
        max_length = 0
        for num in num_set:
            if num - 1 not in num_set:
                current_num = num
                current_length = 1
                while current_num + 1 in num_set:
                    current_num += 1
                    current_length += 1
                max_length = max(max_length, current_length)
        return max_length
```

solution is still *O(n)* and much more robust.
this one passed all the test cases

it works by
> In this code, we use a set `num_set` to efficiently check for the presence of numbers. We iterate through the elements, and if `num - 1` is not in `num_set`, it means `num` is the start of a potential consecutive subsequence. We then increment `current_num` while it exists in `num_set` to find the length of the consecutive subsequence. Finally, we keep track of the maximum length seen so far (`max_length`) and return it after processing all elements. This algorithm has a time complexity of O(n), where n is the length of the input list `nums`.