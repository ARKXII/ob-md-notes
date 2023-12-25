#leetcode 
# summary

Given an integer `x`, return `true` _if_ `x` _is a_ 

_**palindrome**_

_, and_ `false` _otherwise_.

**Example 1:**

**Input:** x = 121
**Output:** true
**Explanation:** 121 reads as 121 from left to right and from right to left.

**Example 2:**

**Input:** x = -121
**Output:** false
**Explanation:** From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.

**Example 3:**

**Input:** x = 10
**Output:** false
**Explanation:** Reads 01 from right to left. Therefore it is not a palindrome.

## thought process

pretty easy problem

convert the number into a string
```python
x_str = str(x)
```

have two pointers traverse the beginning and end of the string
compare the two

```python
i, j = 0, len(x_str) - 1

while i > j:
	if not x_str[i] == x_str[j]: # guard clause that breaks if not equal
		return False
	i += 1
	j -= 1
return True
```

---

another cheeky solution is
```python
x_str = str(x)
return x_str[::-1] == st
```

the trick here is **[::-1]** is a slice notation, a shorthand to reverse the string

here we need not to do any pointers, we just compare if the reversed string is equal to the normal string