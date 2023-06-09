
##  Max Sum Subarray of size K

Given an array of integers Arr of size ```N``` and a number ```K```. ```Return the maximum sum of a subarray of size K.```
 


 


 




**Example 1**
```bash
N = 4, K = 2
Arr = [100, 200, 300, 400]
Output:
700
Explanation:
Arr3  + Arr4 =700,
which is maximum.
```

**Example 2**
```bash
Input:
N = 4, K = 4
Arr = [100, 200, 300, 400]
Output:
1000
Explanation:
Arr1 + Arr2 + Arr3  
+ Arr4 =1000,
which is maximum.
```

### Your Task

You don't need to read input or print anything. Your task is to complete the function maximumSumSubarray() which takes the integer k, vector Arr with size N, containing the elements of the array and returns the maximum sum of a subarray of size K.

**Expected Time Complexity**: O(N)
**Expected Auxiliary Space**: O(1)

### Constraints

- ```1<=N<=106```
- ```1<=K<=N```


## Solution

```javascript
 /**
 * @param {number} K
 * @param {number[]} Arr
 * @param {number} N
 * @return {number}
 */
class Solution {
  maximumSumSubarray(K, Arr, N) {
    let windowSum = 0;
    let maxSum = 0;
    
    for(let i=0;i<K;i++) {
        windowSum += Arr[i];
    }
    
    maxSum = windowSum;
    for(let i=K;i<N;i++) {
        windowSum += Arr[i] - Arr[i-K];
        maxSum = Math.max(windowSum, maxSum);
    }
    
    return maxSum;
  }
}

```
