#hashmap-array 
# summary

Given an array of strings `strs`, group **the anagrams** together. You can return the answer in **any order**.

An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

**Example 1:**

**Input:** strs = ["eat","tea","tan","ate","nat","bat"]
**Output:** [["bat"],["nat","tan"],["ate","eat","tea"]]

**Example 2:**

**Input:** strs = [""]
**Output:** [[""]]

**Example 3:**

**Input:** strs = ["a"]
**Output:** [["a"]]

## thought process

- since it's an anagram problem, the first instinct is to sort each string
- so maybe have a different array and feed the sorted anagrams to
- also have some way of recording what anagram matches with

```python
n = len(strs)
sorted_strs = {}

for i in range(n):
	word = sorted(strs[i])
	 
```

---

- apparently python has an easy way to do this

```python
class Solution:
	def groupAnagrams(self, strs: List[str]) -> List[List[str]]
		anagram_map = defaultdict(list)

		for word in strs:
			sorted_word = ''.join(sorted(word))
			anagram_map[sorted_word].append(word)

		return list(anagram_map.values())
```

from what i understand
```
defaultdict(list)
```
just initializes an ordinary dictionary.

the algorithm works by taking every word and sorting its characters, then appending it to its respective word.
```python
for word in strs:
	sorted_word = ''.join(sorted(word)) # join the sorted letters together
	anagram_map[sorted_word].append(word) # append the letters to current word in map
```
