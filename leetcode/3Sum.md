#two-pointer
# summary

Given an integer array nums, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j`, `i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.

Notice that the solution set must not contain duplicate triplets.

**Example 1:**

**Input:** nums = [-1,0,1,2,-1,-4]
**Output:** [-1,-1,2],[-1,0,1]
**Explanation:** 
nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0.
nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0.
nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0.
The distinct triplets are [-1,0,1] and [-1,-1,2].
Notice that the order of the output and the order of the triplets does not matter.

**Example 2:**

**Input:** nums = [0,1,1]
**Output:** []
**Explanation:** The only possible triplet does not sum up to 0.

**Example 3:**

**Input:** nums = [0,0,0]
**Output:** [0,0,0]
**Explanation:** The only possible triplet sums up to 0.

## thought process

this is quite difficult because of the addition of the third element

```
a + b + c = 0
```

*im not a fan of nested loops so we're not doing that*

we can initialize two pointers
one to get the current number, then another to search the array

one way is to brute force it but i fear that the time and space complexity will be ludicrous, but nevertheless

| -1 | 0 | 1 | 2 | -1 | -4 |

```python
i = 0
j = len(nums) - 1
temp = []

for i in len(nums):
	temp[i] = nums[i] + nums[j]
	# i cant even begin to think how to finish
```

perhaps more research is necessary

---

to solve the duplicates problem, we're going to sort the array first

then for each position, we check behind it to see if it's a duplicate. if it is, then we move forward one position

then we start to think of the algorithm

so we eliminated the duplicates and one element of the 3sum, after that, it's back to the 2sum problem

*reference: [[two sum]] | [[two sum sorted]]*

```python
nums.sort()
result = [] # since we're returning the result as a list of 3 

for i, a in enumerate(nums):
	if i > 0 and a == nums[i - 1]:
		continue # tells the loop to ignore the duplicate

	# two sum 

	left, right = i + 1, len(nums) - 1
	while left < right:
		target = a + nums[left] + nums[right]
		if target > 0:
			right -= 1
		elif target < 0:
			left += 1
		else:
			result.append([a, nums[left], nums[right]])
			left += 1
			while nums[left] == nums[left -1] and left < right:
				left += 1
	return result
```