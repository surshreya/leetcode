## Fruit Into Baskets

You are visiting a farm that has a single row of fruit trees arranged from left to right. The trees are represented by an integer array `fruits` where `fruits[i]` is the **type** of fruit the `ith` tree produces.

You want to collect as much fruit as possible. However, the owner has some strict rules that you must follow:

- You only have **two baskets**, and each basket can only hold a **single type** of fruit. There is no limit on the amount of fruit each basket can hold.
- Starting from any tree of your choice, you must **pick exactly one fruit** from **every tree** (including the start tree) while moving to the right. The picked fruits must fit in one of your baskets.
- Once you reach a tree with fruit that cannot fit in your baskets, you must stop.

Given the integer array fruits, return the **_`maximum number of fruits`_** you can pick.

**Example 1**

```bash
Input: fruits = [1,2,1]
Output: 3
Explanation: We can pick from all 3 trees.
```

**Example 2**

```bash
Input: fruits = [0,1,2,2]
Output: 3
Explanation: We can pick from trees [1,2,2].
If we had started at the first tree, we would only pick from trees [0,1].
```

**Example 3**

```bash
Input: fruits = [1,2,3,2,2]
Output: 4
Explanation: We can pick from trees [2,3,2,2].
If we had started at the first tree, we would only pick from trees [1,2].
```

### Constraints

- `1 <= fruits.length <= 105`
- `0 <= fruits[i] < fruits.length`

## Solution

**_Sliding Window Pattern_**

```javascript
var totalFruit = function (fruits) {
  const mp = new Map();
  let totalfruits = 0;
  let maxFruits = 0;
  let start = 0;

  for (let i = 0; i < fruits.length; i++) {
    mp.set(fruits[i], mp.get(fruits[i]) ? mp.get(fruits[i]) + 1 : 1);
    totalfruits += 1;

    while (mp.size > 2) {
      let fruit = fruits[start];
      mp.set(fruit, mp.get(fruit) - 1);
      totalfruits -= 1;
      start++;

      if (mp.get(fruit) === 0) {
        mp.delete(fruit);
      }
    }
    maxFruits = Math.max(maxFruits, totalfruits);
  }
  return maxFruits;
};
```
