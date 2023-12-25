#hashmap-array 
# summary

Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.

**Example 1:**

**Input:** nums = [1,2,3,1]
**Output:** true

**Example 2:**

**Input:** nums = [1,2,3,4]
**Output:** false

**Example 3:**

**Input:** nums = [1,1,1,3,3,4,3,2,4,2]
**Output:** true

```python
class solution:
	def containsDuplicates(self, nums:List[int]) -> bool:
```

## thought process

- initialize an empty set
```python
mem = set()
```

- loop through the given array, compare each number to numbers in the *mem*
- add the number to the *mem*
- return *true* if num is equal to *mem*
- return *false* if otherwise

```python
class solution:
	def containsDuplicates(self, nums:List[int]) -> bool:
		mem = set()
		for num in nums: 
			if num in mem: #if num is in mem then return true
				return True
			mem.add(num) #add num to mem
		return false
```