
##    Excel Sheet Column Number

Given a string ```columnTitle``` that represents the column title as appears in an Excel sheet, return its ```corresponding column number```.

```
For example:

A -> 1
B -> 2
C -> 3
...
Z -> 26
AA -> 27
AB -> 28 
...
 ```

 


 




**Example 1**
```bash
Input: columnTitle = "A"
Output: 1
```
**Example 2**
```bash
Input: columnTitle = "AB"
Output: 28
```
**Example 3**
```bash
Input: columnTitle = "ZY"
Output: 701
```

### Constraints

- ```1 <= columnTitle.length <= 7```
- ```columnTitle consists only of uppercase English letters.```
- ```columnTitle is in the range ["A", "FXSHRXW"].```
## Solution

```cpp
class Solution {
public:
    int titleToNumber(string columnTitle) {
        int sum = 0;

        for(int i = 0; i < columnTitle.length(); i++) {
            sum = (sum*26) + (columnTitle.at(i) - 64);
        }
        return sum;
    }
};
```

```javascript
var titleToNumber = function(columnTitle) {
    let sum = 0;
    for(let i = 0; i < columnTitle.length; i++) {
        sum = (sum * 26) + (columnTitle.charCodeAt(i)-64);
    }
    return sum;
};
```
