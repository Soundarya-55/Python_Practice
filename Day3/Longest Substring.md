# Problem 3: Longest Substring Without Repeating Characters

**Difficulty:** Medium  
**Topics:** Hash Table, String, Sliding Window  

## Problem Statement

Given a string `s`, find the length of the longest substring without repeating characters.

## Examples

### Example 1:
Input: s = "abcabcbb" Output: 3 Explanation: The answer is "abc", with the length of 3.

### Example 2:
Input: s = "bbbbb" Output: 1 Explanation: The answer is "b", with the length of 1.

```python
class Solution(object):
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        char_index_map = {}
        left = 0
        max_length = 0

        for right in range(len(s)):
            if s[right] in char_index_map and char_index_map[s[right]] >= left:
                left = char_index_map[s[right]] + 1  # move the left pointer
            char_index_map[s[right]] = right
            max_length = max(max_length, right - left + 1)

        return max_length
```
