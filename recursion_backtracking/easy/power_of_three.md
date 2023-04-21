## Power of Three

Given an integer n, return `true` if it is a power of three. Otherwise, return `false`.

An integer n is a power of three, if there exists an integer x such that `n == 3x`.

**Example 1**

```bash
Input: n = 27
Output: true
Explanation: 27 = 3^3
```

**Example 2**

```bash
Input: n = 0
Output: false
Explanation: There is no x where 3^x = 0.
```

**Example 3**

```bash
Input: n = -1
Output: false
Explanation: There is no x where 3^x = (-1).
```

### Constraints

- `-231 <= n <= 231 - 1`

## Solution

```cpp
class Solution {
public:
    bool isPowerOfThree(int n) {
        if(n==1) return true;
        if(n==0) return false;
        if(n%3!=0) return false;
        return isPowerOfThree(n/3);
    }
};
```

```javascript
var isPowerOfThree = function (n) {
  if (n <= 0) return false;

  return Math.pow(3, Math.round(Math.log(n) / Math.log(3))) === n;
};
```
