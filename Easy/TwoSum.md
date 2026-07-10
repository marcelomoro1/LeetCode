# Two Sum

## Problem

Given an array of integers `nums` and an integer `target`, return the **indices** of the two numbers such that they add up to `target`.

### Constraints

* You may assume that each input has **exactly one solution**.
* You may **not use the same element twice**.
* You may return the answer in **any order**.

---

## Solution (Java)

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[i] + nums[j] == target) {
                    return new int[] { i, j };
                }
            }
        }

        return new int[] {};
    }
}
```

---

## Approach

The solution uses two nested loops to compare every possible pair of numbers in the array.

1. Iterate through the array with index `i`.
2. For each `i`, iterate through the remaining elements with index `j`, starting from `i + 1`.
3. Check whether `nums[i] + nums[j]` is equal to `target`.
4. If a matching pair is found, return their indices.
5. The final `return new int[] {};` is included only to satisfy the Java compiler, although the problem guarantees that a solution always exists.

---

## Complexity Analysis

* **Time Complexity:** `O(n²)`
  In the worst case, every pair of elements is checked.

* **Space Complexity:** `O(1)`
  The algorithm uses constant extra space.
