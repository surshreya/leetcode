
##  First Unique Character in a String

Given a string **s**, find the first non-repeating character in it and return its index. If it does not exist, return **-1**.

 
 

 


 




**Example 1**
```bash
Input: s = "leetcode"
Output: 0
```
**Example 2**
```bash
Input: s = "loveleetcode"
Output: 2
```
**Example 3**
```bash
Input: s = "aabb"
Output: -1
```

### Constraints

- ```1 <= s.length <= 105```
- ```s consists of only lowercase English letters.```

    
## Solution

```javascript
var firstUniqChar = function(s) {
    if(!s || s.length === 0) return -1;

    const mp = new Map();
    for(let char of s) {
        mp.set(char, (mp.get(char) || 0) + 1);
    }

    for(let i=0; i<s.length;i++) {
        if(mp.get(s[i]) === 1) {
            return i;
        }
    }
    return -1;    
};
```
