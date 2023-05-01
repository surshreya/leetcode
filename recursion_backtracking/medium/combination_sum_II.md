
##    Combination Sum II

Given a collection of candidate numbers ```(candidates)```  and a target number ``` (target)``` , find  ***```all unique combinations in candidates where the candidate numbers sum to target```*** .

Each number in candidates may ```***only be used once in the combination.```***

**Note:** The solution set must not contain duplicate combinations.

**Example 1**
```bash
Input: candidates = [10,1,2,7,6,1,5], target = 8
Output: 
[
[1,1,6],
[1,2,5],
[1,7],
[2,6]
]
```

**Example 2**
```bash
Input: candidates = [2,5,2,1,2], target = 5
Output: 
[
[1,2,2],
[5]
]
```

### Constraints

- ```1 <= candidates.length <= 30```
- ```2 <= candidates[i] <= 50```
- ```1 <= target <= 30```

## Solution

```javascript
/**
 * @param {number[]} candidates
 * @param {number} target
 * @return {number[][]}
 */
const findCombination = (candidates, target, subset, result, i, n) => {
    if(target === 0) {
        result.push([...subset]);
        return;
    }

    for(let k=i;k<n;k++) {
        if(k > i && candidates[k] === candidates[k-1]) {
            continue;
        }
        if(candidates[k] > target) break;
        subset.push(candidates[k]);
        findCombination(candidates,target-candidates[k],subset,result,k+1,n);
        subset.pop();
    }
}
var combinationSum2 = function(candidates, target) {
    const n = candidates.length;
    const subset = [];
    const result = [];
    candidates.sort((a,b) => a-b);
    findCombination(candidates,target,subset,result,0,n);
    return result;
};
```
