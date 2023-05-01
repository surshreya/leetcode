
##   Subsets

Given an integer array nums of **unique** elements, return ***all possible subsets (the power set).***

The solution set **must not** contain duplicate subsets. Return the solution in **any order**.

 

**Example 1**
```bash
Input: nums = [1,2,3]
Output: [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]
```

**Example 2**
```bash
Input: nums = [0]
Output: [[],[0]]
```

### Constraints

- ```1 <= nums.length <= 10```
- ```-10 <= nums[i] <= 10```
- ```All the numbers of nums are unique.```

## Solution

```javascript

const getSubsets = (i, n, nums, subset, result) => {
    if(i===n) {
        result.push([...subset]);
        return;
    }
    getSubsets(i+1,n,nums,subset,result);
    subset.push(nums[i]);
    getSubsets(i+1,n,nums,subset,result);
    subset.pop();
}
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var subsets = function(nums) {
    const n = nums.length;
    const result = [];
    const subset = [];
    getSubsets(0, n,nums, subset, result);
    return result;
};
```
