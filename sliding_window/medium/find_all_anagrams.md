
##  Find All Anagrams in a String


Given two strings ```s``` and ```p```, return ```an array of all the start indices of p's anagrams in s```. You may return the answer in ***```any order```***.

An ***```Anagram```*** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.
 


 




**Example 1**
```bash
Input: s = "cbaebabacd", p = "abc"
Output: [0,6]
Explanation:
The substring with start index = 0 is "cba", which is an anagram of "abc".
The substring with start index = 6 is "bac", which is an anagram of "abc".
```

**Example 2**
```bash
Input: s = "abab", p = "ab"
Output: [0,1,2]
Explanation:
The substring with start index = 0 is "ab", which is an anagram of "ab".
The substring with start index = 1 is "ba", which is an anagram of "ab".
The substring with start index = 2 is "ab", which is an anagram of "ab".
```

### Constraints

- ```1 <= s.length, p.length <= 3 * 104```
- ```s and p consist of lowercase English letters```

## Solution

```javascript
/**
 * @param {string} s
 * @param {string} p
 * @return {number[]}
 */
var findAnagrams = function(s, p) {
    let sl = s.length;
    let pl = p.length;

    if(pl > sl) return [];
    const result = [];
    const mp = new Map();

    for (const char of p) {
        mp.set(char, (mp.get(char) || 0) + 1);
    }

    let left = 0;
    let right = 0;
    let count = pl;
    while (right < sl) {
        const charRight = s[right];

        if (mp.has(charRight)) {
            mp.set(charRight, mp.get(charRight) - 1);
            if (mp.get(charRight) >= 0) {
                count--;
            }
        }


        if (count === 0) {
            result.push(left);
        }

        if (right - left + 1 === p.length) {
            const charLeft = s[left];

            if (mp.has(charLeft)) {
                mp.set(charLeft, mp.get(charLeft) + 1);
                if (mp.get(charLeft) > 0) {
                    count++;
                }
            }

            left++;
        }

        right++;
    }

  return result;
};
```
