# Q1. Concatenation of Array

## Problem
Given an integer array `nums` of length `n`, return an array `ans` of length `2n` that contains `nums` twice in the same order. In other words, `ans[i] == nums[i]` and `ans[i + n] == nums[i]` for `0 <= i < n`.

### Examples
- `nums = [1, 2, 1]` -> `[1, 2, 1, 1, 2, 1]`
- `nums = [1, 3, 2, 1]` -> `[1, 3, 2, 1, 1, 3, 2, 1]`

### Constraints
- `n == nums.length`
- `1 <= n <= 1000`
- `1 <= nums[i] <= 1000`

## Approach
Create a result array with space for `2n` values. Append every value from `nums` once, then append every value again. The input stays unchanged.

### Steps
1. Create an empty result array with capacity for `2 * nums.length` values.
2. Traverse `nums` from left to right and append each value to the result.
3. Traverse `nums` a second time and append each value again.
4. Return the result.

### Diagram
```text
nums:   [1, 2, 1]
         |  |  |
ans:    [1, 2, 1, 1, 2, 1]
         first copy | second copy
```

## Complexity
- **Time:** `O(n)`; each input value is read twice.
- **Space:** `O(n)` for the returned array of `2n` values.

## C++
```cpp
class Solution {
public:
    vector<int> getConcatenation(vector<int>& nums) {
        vector<int> ans;
        ans.reserve(nums.size() * 2);

        for (int value : nums) {
            ans.push_back(value);
        }
        for (int value : nums) {
            ans.push_back(value);
        }

        return ans;
    }
};
```

## Java
```java
class Solution {
    public int[] getConcatenation(int[] nums) {
        int[] ans = new int[nums.length * 2];
        System.arraycopy(nums, 0, ans, 0, nums.length);
        System.arraycopy(nums, 0, ans, nums.length, nums.length);
        return ans;
    }
}
```

## Python
```python
class Solution:
    def getConcatenation(self, nums: list[int]) -> list[int]:
        return nums + nums
```