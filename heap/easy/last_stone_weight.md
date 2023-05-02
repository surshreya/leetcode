## Last Stone Weight

You are given an array of integers `stones` where `stones[i]` is the weight of the `ith` stone.

We are playing a game with the stones. On each turn, we choose the **heaviest two stones** and smash them together. Suppose the heaviest two stones have weights `x` and `y` with `x <= y`. The result of this smash is:

- If x == y, both stones are destroyed, and
- If x != y, the stone of weight x is destroyed, and the stone of weight y has new weight y - x.

At the end of the game, there is **at most one stone** left.

Return the weight of the last remaining stone. If there are no stones left, return `0`.

**Example 1**

```bash
Input: stones = [2,7,4,1,8,1]
Output: 1
Explanation:
We combine 7 and 8 to get 1 so the array converts to [2,4,1,1,1] then,
we combine 2 and 4 to get 2 so the array converts to [2,1,1,1] then,
we combine 2 and 1 to get 1 so the array converts to [1,1,1] then,
we combine 1 and 1 to get 0 so the array converts to [1] then that's the value of the last stone.
```

**Example 2**

```bash
Input: stones = [1]
Output: 1
```

### Constraints

- `1 <= stones.length <= 30`
- `1 <= stones[i] <= 1000`

## Solution

**_`Solution 1`_**

```javascript
/**
 * @param {number[]} stones
 * @return {number}
 */
var lastStoneWeight = function (stones) {
  while (stones.length > 1) {
    let a = Math.max(...stones);
    stones.splice(stones.indexOf(a), 1);
    let b = Math.max(...stones);
    stones.splice(stones.indexOf(b), 1);
    if (a !== b) {
      stones.push(a - b);
    }
  }

  if (stones.length === 0) return 0;
  return stones[0];
};
```

**_`Solution 2`_**

```javascript
/**
 * @param {number[]} stones
 * @return {number}
 */
var lastStoneWeight = function (stones) {
  const pq = new MaxPriorityQueue({ priority: (stone) => stone });
  stones.forEach((stone) => pq.enqueue(stone));

  while (pq.size() > 1) {
    const a = pq.dequeue().element;
    const b = pq.dequeue().element;
    if (a !== b) {
      pq.enqueue(a - b);
    }
  }

  return pq.size() === 0 ? 0 : pq.dequeue().element;
};
```
