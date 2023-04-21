## Maximum Average Subarray I

You are given an integer array nums consisting of `n` elements, and an integer `k`.

Find a contiguous subarray whose **length is equal to k** that has the maximum average value and return this value. Any answer with a calculation error less than `10^-5` will be accepted.

**Example 1**

```bash
Input: nums = [1,12,-5,-6,50,3], k = 4
Output: 12.75000
Explanation: Maximum average is (12 - 5 - 6 + 50) / 4 = 51 / 4 = 12.75
```

**Example 2**

```bash
Input: nums = [5], k = 1
Output: 5.00000
```

### Constraints

- `n == nums.length`
- `1 <= n <= 5 * 105`
- `-104 <= nums[i] <= 104`

## Solution

**_Sliding Window Pattern_**

```javascript
var findMaxAverage = function (nums, k) {
  let maxSum = 0;
  let windowSum = 0;

  /* calculate sum of 1st window */
  for (let i = 0; i < k; i++) {
    windowSum += nums[i];
  }

  maxSum = windowSum;

  /* Start the window from the left (k instead of 0), 
    remove leftmost and add right to get current window calculation*/
  for (let i = k; i < nums.length; i++) {
    windowSum += nums[i] - nums[i - k];
    maxSum = Math.max(maxSum, windowSum);
  }

  return maxSum / k;
};
```
