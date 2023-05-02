
##   Top K Frequent Elements

Given an integer array ```nums``` and an integer ```k```, return the ```k most frequent elements```. You may return the answer in **any order**.

**Example 1**
```bash
Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]
```

**Example 2**
```bash
Input: nums = [1], k = 1
Output: [1]
```

### Constraints

- ```1 <= nums.length <= 105```
- ```-104 <= nums[i] <= 104```
- ```k is in the range [1, the number of unique elements in the array].```
- ```It is guaranteed that the answer is unique.```

## Solution

***``` Solution 1 ```***
```javascript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number[]}
 */
var topKFrequent = function(nums, k) {
    const frequency = {};
    nums.forEach(num => {
        frequency[num] = (frequency[num] || 0) + 1;
    });

    const sorted = Object.entries(frequency).sort((a,b) => b[1] - a[1]);
    return sorted.slice(0, k).map(val => val[0]);
};
```

***``` Solution 2 ```***
```javascript

/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number[]}
 */
var topKFrequent = function(nums, k) {
    const frequency = {};
    for (const num of nums) {
        frequency[num] = (frequency[num] || 0) + 1;
    }

   const pq = new MaxPriorityQueue({
       priority: ([num, freq])=> freq
   });

    for (const [num, freq] of Object.entries(frequency)) {
        pq.enqueue([num, freq]);
    }

    const result = [];
    for (let i = 0; i < k; i++) {
        result.push(Number(pq.dequeue().element[0]));
    }
    return result;
};
```

***``` Solution 3 ```***
```javascript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number[]}
 */
var topKFrequent = function(nums, k) {
    const frequency = {};
    nums.forEach(num => {
        frequency[num] = (frequency[num] || 0) + 1;
    });

    const buckets = [];
    for (const [num, freq] of Object.entries(frequency)) {
       if(!buckets[freq]) {
           buckets[freq] = [];
       }
       buckets[freq].push(parseInt(num));
    }

    const result = [];
    for (let i = buckets.length - 1; i >= 0 && result.length < k; i--) {
        if (buckets[i]) {
            result.push(...buckets[i]);
        }
    }

    return result;
};
```
