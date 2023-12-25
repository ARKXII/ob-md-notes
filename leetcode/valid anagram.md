#hashmap-array 
# summary

Given two strings `s` and `t`, return `true` _if_ `t` _is an anagram of_ `s`_, and_ `false` _otherwise_.

An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

**Example 1:**

**Input:** s = "anagram", t = "nagaram"
**Output:** true

**Example 2:**

**Input:** s = "rat", t = "car"
**Output:** false

**Constraints:**

- `1 <= s.length, t.length <= 5 * 104`
- `s` and `t` consist of lowercase English letters.

## thought process

- simplest way might be to sort the two strings then compare
- something like:

```python
s str
t str

sort(s)
sort(t)

if s == t:
	return true
```

- i was on the right track

```python
class solution:
	def validAnagram(self, t: str, s: str) -> bool:
		sorted_t = sorted(t)
		sorted_s = sorted(s)

		return sorted_t == sorted_s
```

- another cheap trick using python lib

```python
import collections
class solution:
	def isAnagram(self, t: str, s: str) -> bool:
		return collections.Counter(s) == collections.Counter(t)
```