#hashmap-array
# summary

Given an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_.

You may assume that each input would have **_exactly_ one solution**, and you may not use the _same_ element twice.

You can return the answer in any order.

**Example 1:**

**Input:** nums = [2,7,11,15], target = 9
**Output:** [0,1]
**Explanation:** Because nums[0] + nums[1] == 9, we return [0, 1].

**Example 2:**

**Input:** nums = [3,2,4], target = 6
**Output:** [1,2]

**Example 3:**

**Input:** nums = [3,3], target = 6
**Output:** [0,1]

## thought process

- create an empty hash table
- iterate through the array
- check if *i - target* exists in the array
- if it does, it's the correct answer
- if not, add *i* to table

```python
class Solution:
	def twoSum(self, nums: List[int], target: int) -> List[int]
		hashMap = {} #declare hashmap
		n = len(nums) #get range of nums array

		for i in range(n):
			x = target - nums[i] 
			if x in hashMap:
				return [hashMap[x], i] 
			hashMap[nums[i]] = i #if not found, add num to hashMap
		return []
```