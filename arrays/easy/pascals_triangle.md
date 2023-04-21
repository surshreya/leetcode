
##  Pascal's Triangle

Given an integer numRows, return the first numRows of Pascal's triangle.

![PascalTriangleAnimated2](https://user-images.githubusercontent.com/118065908/233125922-0f8e5a51-97df-4fda-9211-b845dfde8083.gif)


In Pascal's triangle, each number is the sum of the two numbers directly above it as shown:



 




**Example 1**
```bash
Input: numRows = 5
Output: [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]
```
**Example 2**
```bash
Input: numRows = 1
Output: [[1]]
```
    
### Constraints

- ```1 <= numRows <= 30```



## Solution

```javascript
 var generate = function(numRows) {
    if(numRows === 0) return [];

    const A = [];
    for(let i = 0; i < numRows; i++) {
        A[i] = [];
        A[i][0] = 1;
        A[i][i] = 1;

        for(let j = 1; j < i; j++) {
            A[i][j] = A[i-1][j] + A[i-1][j-1];
        }
    }
    return A;
};
```
