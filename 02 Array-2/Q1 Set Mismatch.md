# Q1. Set Mismatch

## Problem
An array should contain every integer from `1` to `n` exactly once. One value appears twice and another is missing. Given `nums`, return `[duplicate, missing]`.

### Examples
- `nums = [1, 2, 2, 4]` -> `[2, 3]`
- `nums = [1, 1]` -> `[1, 2]`

### Constraints
- `2 <= nums.length <= 10^4`
- `1 <= nums[i] <= 10^4`

## Approach
Use a frequency array where index `i` stores how many times value `i` appears. A frequency of `2` identifies the duplicate; a frequency of `0` identifies the missing value.

### Steps
1. Let `n` be `nums.length` and create a frequency array of size `n + 1`.
2. Count each value in `nums` at its corresponding frequency index.
3. Scan values from `1` through `n`.
4. Save the value with frequency `2` as the duplicate and the value with frequency `0` as the missing value.
5. Return `[duplicate, missing]` in that order.

### Diagram
```text
nums:       [1, 2, 2, 4]
frequency:   1  2  0  1   (indices 1 through 4)
                 |  |
duplicate:       2  missing: 3
```

## Complexity
- **Time:** `O(n)`; one pass counts values and one pass checks frequencies.
- **Space:** `O(n)` for the frequency array.

## C++
```cpp
class Solution {
public:
    vector<int> findErrorNums(vector<int>& nums) {
        int n = nums.size();
        vector<int> frequency(n + 1, 0);

        for (int value : nums) {
            ++frequency[value];
        }

        int duplicate = 0;
        int missing = 0;
        for (int value = 1; value <= n; ++value) {
            if (frequency[value] == 2) {
                duplicate = value;
            } else if (frequency[value] == 0) {
                missing = value;
            }
        }

        return {duplicate, missing};
    }
};
```

## Java
```java
class Solution {
    public int[] findErrorNums(int[] nums) {
        int n = nums.length;
        int[] frequency = new int[n + 1];

        for (int value : nums) {
            frequency[value]++;
        }

        int duplicate = 0;
        int missing = 0;
        for (int value = 1; value <= n; value++) {
            if (frequency[value] == 2) {
                duplicate = value;
            } else if (frequency[value] == 0) {
                missing = value;
            }
        }

        return new int[] {duplicate, missing};
    }
}
```

## Python
```python
class Solution:
    def findErrorNums(self, nums: list[int]) -> list[int]:
        n = len(nums)
        frequency = [0] * (n + 1)

        for value in nums:
            frequency[value] += 1

        duplicate = 0
        missing = 0
        for value in range(1, n + 1):
            if frequency[value] == 2:
                duplicate = value
            elif frequency[value] == 0:
                missing = value

        return [duplicate, missing]
```