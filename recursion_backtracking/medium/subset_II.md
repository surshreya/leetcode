
##   Subsets II

Given an integer array nums that **may contain duplicates**, return **all possible 
subsets (the power set).**

The solution set **must not** contain duplicate subsets. Return the solution in **any order**.

**Example 1**
```bash
Input: nums = [1,2,2]
Output: [[],[1],[1,2],[1,2,2],[2],[2,2]]
```

**Example 2**
```bash
Input: nums = [0]
Output: [[],[0]]
```

### Constraints

- ```1 <= nums.length <= 10```
- ```-10 <= nums[i] <= 10```

## Solution

```javascript
/**
 * @param {number[]} nums
 * @return {number[][]}
 */

const getSubset = (i,n,nums,subset,result) => {
    result.push([...subset]);
    for(let k=i; k<n; k++) {
        if(k>i && nums[k] === nums[k-1]) continue;
        subset.push(nums[k]);
        getSubset(k+1,n,nums,subset,result);
        subset.pop();
    }
}

var subsetsWithDup = function(nums) {
    const n = nums.length;
    const result = [];
    const subset = [];
    nums.sort((a,b)=>a-b);
    getSubset(0,n,nums,subset,result);
    return result;
};
```
