# Two Sum

## Problem

Given an array of integers `nums` and an integer `target`, return the indices of the two numbers such that they add up to `target`.

You may assume that each input has exactly one solution.

You may not use the same element twice.

You can return the answer in any order.

## Examples

### Example 1

**Input:**

    nums = [2, 7, 11, 15]
    target = 9

**Output:**

    [0, 1]

**Explanation:**

    nums[0] + nums[1] = 2 + 7 = 9

Therefore, the answer is `[0, 1]`.

### Example 2

**Input:**

    nums = [3, 2, 4]
    target = 6

**Output:**

    [1, 2]

**Explanation:**

    nums[1] + nums[2] = 2 + 4 = 6

Therefore, the answer is `[1, 2]`.

### Example 3

**Input:**

    nums = [3, 3]
    target = 6

**Output:**

    [0, 1]

**Explanation:**

    nums[0] + nums[1] = 3 + 3 = 6

Therefore, the answer is `[0, 1]`.

## Approach

We use a **Hash Map (Dictionary)** to solve the problem efficiently.

For every number in the array, we calculate the number required to reach the target.

    complement = target - current_number

Then we check whether this complement already exists in the dictionary.

If it exists, we have found the two required numbers.

If it does not exist, we store the current number and its index in the dictionary.

## Algorithm

1. Create an empty dictionary called `seen`.
2. Loop through the array using `enumerate()`.
3. For each number, calculate:

       complement = target - num

4. Check if `complement` is already present in `seen`.
5. If it is present, return the stored index and current index.
6. If it is not present, store the current number and its index.
7. Continue until the answer is found.

## Step-by-Step Example

Consider:

    nums = [2, 7, 11, 15]
    target = 9

### Step 1

Current number:

    2

Required complement:

    9 - 2 = 7

`7` is not in the dictionary.

Store:

    seen = {
        2: 0
    }

### Step 2

Current number:

    7

Required complement:

    9 - 7 = 2

`2` is already in the dictionary at index `0`.

The current number `7` is at index `1`.

Therefore:

    [0, 1]

is the answer.

## Python Solution

    from typing import List


    class Solution:
        def twoSum(self, nums: List[int], target: int) -> List[int]:
            seen = {}

            for i, num in enumerate(nums):
                complement = target - num

                if complement in seen:
                    return [seen[complement], i]

                seen[num] = i

            return []

## Complexity Analysis

### Time Complexity

    O(n)

We traverse the array only once.

Dictionary lookup takes `O(1)` average time.

Therefore, the overall time complexity is `O(n)`.

### Space Complexity

    O(n)

In the worst case, we may store every element in the dictionary.

## Key Concept

The main idea is:

    current number + complement = target

Therefore:

    complement = target - current number

Using a dictionary allows us to find the required complement efficiently instead of checking every possible pair.

## Topics

- Array
- Hash Table
- Dictionary
- Two Sum
- LeetCode
- Python
- Problem Solving

## Difficulty

Easy

## LeetCode

Problem Number: 1

Problem Name: Two Sum
