
# Running Sum of 1d Array

Given an array nums. We define a running sum of an array as runningSum[i] = sum(nums[0]…nums[i]).

Return the running sum of nums.




**Example 1**
```bash
  Input: nums = [1,2,3,4]
  Output: [1,3,6,10]
  Explanation: Running sum is obtained as follows: [1, 1+2, 1+2+3, 1+2+3+4].
```
**Example 2**
```bash
  Input: nums = [1,1,1,1,1]
  Output: [1,2,3,4,5]
  Explanation: Running sum is obtained as follows: [1, 1+1, 1+1+1, 1+1+1+1, 1+1+1+1+1].
```
**Example 3**
```bash
  Input: nums = [3,1,2,10,1]
  Output: [3,4,6,16,17]
```
    
### Constraints

```1 <= nums.length <= 10^4```

```-1000 <= nums[i] <= 1000```

## Solution

```javascript
var runningSum = function(nums) {
    if(!nums || nums.length === 0) return;

    const result = [nums[0]];
    for(let i=1;i<nums.length;i++) {
        result.push(result[i-1]+nums[i]);
    }

    return result;
};

```
