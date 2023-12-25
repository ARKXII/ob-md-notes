#two-pointer 
# summary

A phrase is a **palindrome** if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string `s`, return `true` _if it is a **palindrome**, or_ `false` _otherwise_.

**Example 1:**

**Input:** s = "A man, a plan, a canal: Panama"
**Output:** true
**Explanation:** "amanaplanacanalpanama" is a palindrome.

**Example 2:**

**Input:** s = "race a car"
**Output:** false
**Explanation:** "raceacar" is not a palindrome.

**Example 3:**

**Input:** s = " "
**Output:** true
**Explanation:** s is an empty string "" after removing non-alphanumeric characters.
Since an empty string reads the same forward and backward, it is a palindrome.

---
## thought process

since the problem wants us to only consider the alphanumeric characters and ignore the cases, best thing to do first is convert both strings in a singular case i.e. *upper* or *lower* case

i need to also get rid of any symbols that appears in the words or whitespaces such that:

```python
string = "Hello World!"
clean(string) # clean the string

string = "helloworld"
```

so a function to clean the string should come first

```python
import re

def clean_up_string(input_string):
    # Remove symbols and whitespaces using regex
    cleaned_string = re.sub(r'[^a-zA-Z0-9]', '', input_string)
    
    # Convert to lowercase
    cleaned_string = cleaned_string.lower()
    
    return cleaned_string

# Example usage:
input_string = "Hello, World! 123"
cleaned_result = clean_up_string(input_string)
print(cleaned_result)  # Output: "helloworld123"
```

then a reverse loop to flip *string* around

```python
for i in range(len(n)-1, -1, -1):
	output_string[i] = string2[i]

# something like this. im still not sure yet
# this might fail at some testcases
```

---

upon closer reading, the problem itself is a two pointer problem, so it makes more sense to use two pointers to traverse the string

these two pointers store whatever character they are pointing at into their respective arrays
```python
left_pointer = 0
right_pointer = len(string) - 1

while right_pointer >= left_pointer:
	if string[left_pointer] == string[right_pointer]:
		left_pointer += 1
		right_pointer -= 1
	else
		break
		return False
	return True
```

---

```python
import re

class Solution:

    def cleanString(self, s: str) -> string:

       cleaned_string = re.sub(r'[^a-zA-Z0-9]', '', s)

       cleaned_string = cleaned_string.lower()

  

       return cleaned_string

  

    def isPalindrome(self, s: str) -> bool:

      palindrome = self.cleanString(s)

  

      left_pointer = 0

      right_pointer = len(palindrome) - 1

  

      while right_pointer >= left_pointer:

        if palindrome[left_pointer] == palindrome[right_pointer]:

                left_pointer += 1

                right_pointer -= 1

        else:

            return False

        return True
```

im trouble with empty strings "" and "race a car"

---

well turns out im right and it's just a python indentation thing

```python
import re

class Solution:

    def cleanString(self, s: str) -> string:

       cleaned_string = re.sub(r'[^a-zA-Z0-9]', '', s)

       cleaned_string = cleaned_string.lower()

  

       return cleaned_string

  

    def isPalindrome(self, s: str) -> bool:

      palindrome = self.cleanString(s)

  

      left_pointer = 0

      right_pointer = len(palindrome) - 1

  

      while right_pointer >= left_pointer:

        if palindrome[left_pointer] == palindrome[right_pointer]:

                left_pointer += 1

                right_pointer -= 1

        else:

            return False
	      return True
```