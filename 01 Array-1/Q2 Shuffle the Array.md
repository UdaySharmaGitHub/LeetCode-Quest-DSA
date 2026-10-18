Q2. Shuffle the Array
Given the array nums consisting of 2n elements in the form [x1,x2,...,xn,y1,y2,...,yn].

Return the array in the form [x1,y1,x2,y2,...,xn,yn].

 

Example 1:

Input: nums = [2,5,1,3,4,7], n = 3
Output: [2,3,5,4,1,7] 
Explanation: Since x1=2, x2=5, x3=1, y1=3, y2=4, y3=7 then the answer is [2,3,5,4,1,7].
Example 2:

Input: nums = [1,2,3,4,4,3,2,1], n = 4
Output: [1,4,2,3,3,2,4,1]
Example 3:

Input: nums = [1,1,2,2], n = 2
# Q2. Shuffle the Array

## Problem
The array `nums` contains `2n` values arranged as `[x1, x2, ..., xn, y1, y2, ..., yn]`. Return the values interleaved as `[x1, y1, x2, y2, ..., xn, yn]`.

### Examples
- `nums = [2,  5,  1,  3,  4,  7]`, `n = 3` -> `[2, 3, 5, 4, 1, 7]`
- `nums = [1, 2, 3, 4, 4, 3, 2, 1]`, `n = 4` -> `[1, 4, 2, 3, 3, 2, 4, 1]`
- `nums = [1, 1, 2, 2]`, `n = 2` -> `[1, 2, 1, 2]`

### Constraints
- `1 <= n <= 500`
- `nums.length == 2n`
- `1 <= nums[i] <= 1000`

## Approach
The first half contains the `x` values and the second half contains the matching `y` values. For each index `i` in the first half, append `nums[i]` followed by `nums[i + n]`.

### Steps
1. Create an empty result array with capacity for all `2n` values.
2. Loop over `i` from `0` through `n - 1`.
3. Append `nums[i]` (the next `x`) and then `nums[i + n]` (the matching `y`).
4. Return the result.

### Diagram
```text
index:   0  1  2 | 3  4  5
nums:   [2, 5, 1 | 3, 4, 7]
         x1 x2 x3  y1 y2 y3
           |  |     |  |     |
ans:    [ 2, 3,  5, 4,  1, 7 ]
```

## Complexity
- **Time:** `O(n)`; the loop processes each pair once.
- **Space:** `O(n)` for the returned array containing `2n` values.

## C++
```cpp
class Solution {
public:
    vector<int> shuffle(vector<int>& nums, int n) {
        vector<int> ans;
        ans.reserve(nums.size());

        for (int i = 0; i < n; ++i) {
            ans.push_back(nums[i]);
            ans.push_back(nums[i + n]);
        }

        return ans;
    }
};
```

## Java
```java
class Solution {
    public int[] shuffle(int[] nums, int n) {
        int[] ans = new int[nums.length];

        for (int i = 0; i < n; i++) {
            ans[2 * i] = nums[i];
            ans[2 * i + 1] = nums[i + n];
        }

        return ans;
    }
}
```

## Python
```python
class Solution:
    def shuffle(self, nums: list[int], n: int) -> list[int]:
        ans = []

        for i in range(n):
            ans.append(nums[i])
            ans.append(nums[i + n])

        return ans
```