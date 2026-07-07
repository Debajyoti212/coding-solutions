# Median of Two Sorted Arrays

![Difficulty](https://img.shields.io/badge/Difficulty-Hard-red)

## Problem

Given two sorted arrays `nums1` and `nums2` of size `m` and `n` respectively, return  **the median**  of the two sorted arrays.

The overall run time complexity should be `O(log (m+n))`.

 

 **Example 1:** 

```
Input: nums1 = [1,3], nums2 = [2]
Output: 2.00000
Explanation: merged array = [1,2,3] and median is 2.

```

 **Example 2:** 

```
Input: nums1 = [1,2], nums2 = [3,4]
Output: 2.50000
Explanation: merged array = [1,2,3,4] and median is (2 + 3) / 2 = 2.5.

```

 

 **Constraints:** 

- nums1.length == m
- nums2.length == n
- 0 <= m <= 1000
- 0 <= n <= 1000
- 1 <= m + n <= 2000
- -106 <= nums1[i], nums2[i] <= 106

## Solution

**Language:** Python  
**Runtime:** 0 ms (beats 100.00%)  
**Memory:** 19.7 MB (beats 14.52%)  
**Submitted:** 2026-07-07T14:34:46.560Z  

```py
class Solution:
    def findMedianSortedArrays(self, nums1, nums2):
        A, B = nums1, nums2
        total = len(A) + len(B)
        half = total // 2
        
        if len(B) < len(A):
            A, B = B, A
            
        low, high = 0, len(A)
        
        while low <= high:
            i = (low + high) // 2
            j = half - i
            
            A_left = A[i - 1] if i > 0 else float('-inf')
            A_right = A[i] if i < len(A) else float('inf')
            
            B_left = B[j - 1] if j > 0 else float('-inf')
            B_right = B[j] if j < len(B) else float('inf')
            
            if A_left <= B_right and B_left <= A_right:
                if total % 2 != 0:
                    return min(A_right, B_right)
                return (max(A_left, B_left) + min(A_right, B_right)) / 2
                
            elif A_left > B_right:
                high = i - 1
            else:
                low = i + 1
```

---

[View on LeetCode](https://leetcode.com/problems/median-of-two-sorted-arrays/)