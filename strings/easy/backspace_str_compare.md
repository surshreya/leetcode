
##  Backspace String Compare

Given two strings ```s``` and ```t```, return ```true``` if they are equal when both are typed into empty text editors. ```'#'``` means a backspace character.

Note that after backspacing an empty text, the text will continue empty.
 


 




**Example 1**
```bash
Input: s = "ab#c", t = "ad#c"
Output: true
Explanation: Both s and t become "ac".
```

**Example 2**
```bash
Input: s = "ab##", t = "c#d#"
Output: true
Explanation: Both s and t become "".
```

**Example 3**
```bash
Input: s = "a#c", t = "b"
Output: false
Explanation: s becomes "c" while t becomes "b".
```

### Constraints

- ```1 <= s.length, t.length <= 200```
- ```s and t only contain lowercase letters and '#' characters.```

## Solution

***```Solution 1```***
```javascript
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var backspaceCompare = function(s, t) {
    const sNew = [];
    const tNew = [];

    for(let i=0;i<s.length;i++) {
        s[i] === '#' ? sNew.pop() : sNew.push(s[i]);
    }

    for(let i=0;i<t.length;i++) {
        t[i] === '#' ? tNew.pop() : tNew.push(t[i]);
    }

    return sNew.join('') === tNew.join('');

};
```
***```Solution 2 - Efficient```***

```javascript

/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var backspaceCompare = function(s, t) {
    let i = s.length - 1;
    let j = t.length - 1;

    let sMove = 0, tMove = 0;
    while(i>=0 || j>=0){
        if(s[i] === '#') {
            sMove++;
            i--;
        } else if(sMove > 0 && i>=0) {
            sMove--;
            i--;
        } else if(t[j] === '#') {
            tMove++;
            j--;
        } else if(tMove > 0 && j>=0) {
            tMove--;
            j--;
        } else if(s[i] !== t[j]) {
            return false;
        } else {
            i--;
            j--;
        }

    }
    return true;

};
```
