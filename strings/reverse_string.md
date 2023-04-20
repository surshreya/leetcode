
##  Reverse String

Write a function that reverses a string. The input string is given as an array of characters s.

You must do this by modifying the input array **in-place** with O(1) extra memory.

 
 

 


 




**Example 1**
```bash
Input: s = ["h","e","l","l","o"]
Output: ["o","l","l","e","h"]
```
**Example 2**
```bash
Input: s = ["H","a","n","n","a","h"]
Output: ["h","a","n","n","a","H"]
```

### Constraints

- ```1 <= s.length <= 105```
- ```s[i] is a printable ascii character.```

    
## Solution

```cpp
class Solution {
public:
    void reverseString(vector<char>& s) {
        int n = s.size(), i = 0, j = n-1;
        while(i<j) {
            swap(s[i], s[j]);
            i++;
            j--;
        }
    }
};
```
```javascript
var reverseString = function(s) {
    return s.reverse();
};
```
