# Q3. Max Consecutive Ones

## Problem
Given a binary array `nums`, return the maximum number of consecutive `1`s in the array.

### Examples
- `nums = [1, 1, 0, 1, 1, 1]` -> `3`
- `nums = [1, 0, 1, 1, 0, 1]` -> `2`

### Constraints
- `1 <= nums.length <= 10^5`
- `nums[i]` is either `0` or `1`.

## Approach
Scan the array once while tracking the current streak of `1`s and the longest streak seen so far. A `0` ends the current streak, so update the maximum and reset the current count. Check the maximum again after the loop to include a streak that reaches the end.

### Steps
1. Initialize `current` and `best` to `0`.
2. For each value, increment `current` when it is `1`.
3. When the value is `0`, update `best` with `current`, then reset `current` to `0`.
4. After the loop, return the larger of `best` and `current`.

### Diagram
```text
nums:     [1, 1, 0, 1, 1, 1]
current:   1  2  0  1  2  3
best:      1  2  2  2  2  3
```

## Complexity
- **Time:** `O(n)`; each value is visited once.
- **Space:** `O(1)`; only two counters are used.

## C++
```cpp
class Solution {
public:
    int findMaxConsecutiveOnes(vector<int>& nums) {
        int current = 0;
        int best = 0;

        for (int value : nums) {
            if (value == 1) {
                ++current;
                best = max(best, current);
            } else {
                current = 0;
            }
        }

        return best;
    }
};
```

## Java
```java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int current = 0;
        int best = 0;

        for (int value : nums) {
            if (value == 1) {
                current++;
                best = Math.max(best, current);
            } else {
                current = 0;
            }
        }

        return best;
    }
}
```

## Python
```python
class Solution:
    def findMaxConsecutiveOnes(self, nums: list[int]) -> int:
        current = 0
        best = 0

        for value in nums:
            if value == 1:
                current += 1
                best = max(best, current)
            else:
                current = 0

        return best
```