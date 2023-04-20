
##   Contains Duplicate

Given an integer array nums, return ```true``` if any value appears **at least twice** in the array, and return ```false``` if every element is distinct.

 
 
 

 


 




**Example 1**
```bash
Input: nums = [1,2,3,1]
Output: true
```
**Example 2**
```bash
Input: nums = [1,2,3,4]
Output: false
```

**Example 3**
```bash
Input: nums = [1,1,1,3,3,4,3,2,4,2]
Output: true
```

### Constraints

- ```1 <= nums.length <= 105```
- ```-109 <= nums[i] <= 109```

## Solution

```javascript
var containsDuplicate = function(nums) {
    if(!nums || nums.length === 0) return false;

    const mp = new Map();
    for(let i = 0; i < nums.length; i++) {
        if(mp.has(nums[i])) {
            mp.set(nums[i], mp.get(nums[i]) + 1);
            if (mp.get(nums[i]) > 1) {
                return true;
            }
        } else {
            mp.set(nums[i], 1);
        }
    }
    return false;
};
```
