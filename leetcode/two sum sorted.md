#two-pointer 
# summary

Given a **1-indexed** array of integers `numbers` that is already **_sorted in non-decreasing order_**, find two numbers such that they add up to a specific `target` number. Let these two numbers be `numbers[index1]` and `numbers[index2]` where `1 <= index1 < index2 < numbers.length`.

Return _the indices of the two numbers,_ `index1` _and_ `index2`_, **added by one** as an integer array_ `[index1, index2]` _of length 2._

The tests are generated such that there is **exactly one solution**. You **may not** use the same element twice.

Your solution must use only constant extra space.

**Example 1:**

**Input:** numbers = [2,7,11,15], target = 9
**Output:** [1,2]
**Explanation:** The sum of 2 and 7 is 9. Therefore, index1 = 1, index2 = 2. We return [1, 2].

**Example 2:**

**Input:** numbers = [2,3,4], target = 6
**Output:** [1,3]
**Explanation:** The sum of 2 and 4 is 6. Therefore index1 = 1, index2 = 3. We return [1, 3].

**Example 3:**

**Input:** numbers = [-1,0], target = -1
**Output:** [1,2]
**Explanation:** The sum of -1 and 0 is -1. Therefore index1 = 1, index2 = 2. We return [1, 2].

## thought process

looking at the write ups, there's the concern that we must only have a space complexity of O(1)

going forward, a hash map would probably be in violation of this, so we continue with two pointers

```python
i = 0
j = len(nums) - 1

while nums[i] + nums[j] != target:
	sum = nums[i] + nums[j]
	if sum > target:
		j -= 1
	else:
		i += 1
return [i + 1, j + 1]	
```

the constraint of the problem is that it *only has one solution* and it is also *sorted*

given that, we can logically move our pointers relative to the target