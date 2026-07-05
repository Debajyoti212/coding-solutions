# Longest Substring Without Repeating Characters

![Difficulty](https://img.shields.io/badge/Difficulty-Medium-yellow)

## Problem

Given a string `s`, find the length of the  **longest**   **substring**  without duplicate characters.

 

 **Example 1:** 

```
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3. Note that "bca" and "cab" are also correct answers.

```

 **Example 2:** 

```
Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.

```

 **Example 3:** 

```
Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.

```

 

 **Constraints:** 

- 0 <= s.length <= 5 * 104
- s consists of English letters, digits, symbols and spaces.

## Solution

**Language:** Python  
**Runtime:** 33 ms (beats 23.59%)  
**Memory:** 13.2 MB (beats 22.92%)  
**Submitted:** 2026-07-05T19:34:56.268Z  

```py
class Solution:
    def lengthOfLongestSubstring(self, s):

        charSet = set()
        left = 0
        maxLen = 0

        for right in range(len(s)):
            while s[right] in charSet:
                charSet.remove(s[left])
                left += 1

            charSet.add(s[right])
            maxLen = max(maxLen, right - left + 1)

        return maxLen
```

---

[View on LeetCode](https://leetcode.com/problems/longest-substring-without-repeating-characters/)