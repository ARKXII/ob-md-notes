#stack
# summary

Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.
3. Every close bracket has a corresponding open bracket of the same type.

**Example 1:**

**Input:** s = "()"
**Output:** true

**Example 2:**

**Input:** s = "()[]{}"
**Output:** true

**Example 3:**

**Input:** s = "(]"
**Output:** false

## thought process

i think we should proceed with using some type of sort function if it's even possible to sort symbols

```python
class Solution:

    def isValid(self, s: str) -> bool:

        print(sorted(s))
```

okay this works. so it should be pretty easy

so initialize a stack to feed in the string

```python
 class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        brackets = {'(':')', '{':'}','[':']'}
        for c in s:
            if c in brackets:
                stack.append(c)
            elif stack and c == brackets[stack.pop()]:
                continue
            else:
                return False
        return not stack
```