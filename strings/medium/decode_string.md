
##  Decode String

Given an encoded string, return its decoded string.

The encoding rule is: ```k[encoded_string]```, where the encoded_string inside the square brackets is being repeated exactly k times. Note that ```k``` is guaranteed to be a positive integer.

You may assume that the input string is always valid; there are no extra white spaces, square brackets are well-formed, etc. Furthermore, you may assume that the original data does not contain any digits and that digits are only for those repeat numbers, k. For example, there will ```not``` be input like ```3a``` or ```2[4]```.

The test cases are generated so that the length of the output will never exceed ```105```.

 




**Example 1**
```bash
Input: s = "2[abc]3[cd]ef"
Output: "abcabccdcdcdef"
```

**Example 2**
```bash
Input: s = "3[a]2[bc]"
Output: "aaabcbc"
```

**Example 3**
```bash
Input: s = "3[a2[c]]"
Output: "accaccacc"
```

### Constraints

- ```1 <= s.length <= 30```
- ```s consists of lowercase English letters, digits, and square brackets '[]'.```
- ```s is guaranteed to be a valid input```
- ```All the integers in s are in the range [1, 300].```
## Solution

```javascript
/**
 * @param {string} s
 * @return {string}
 */
var decodeString = function(s) {
    let stack = [];

    for(let i=0; i<s.length;i++) {
        let char = s[i];
        if(char === ']') {
            let str = '';
            while(stack.at(-1) !== '[') {
                str = stack.pop() + str;
            }
            stack.pop(); // pop the [ bracket
            let repeatNum = stack.pop();
            while(!isNaN(stack.at(-1))) {
                repeatNum = stack.pop() + repeatNum;
            }
            stack.push(str.repeat(repeatNum));
        } else {
            stack.push(char);
        }
    }
    return stack.join('');
};
```
