## Unique Paths

You are given an integer array `cost` where `cost[i]` is the cost of `ith` step on a staircase. Once you pay the cost, you can either climb one or two steps.

You can either start from the step with index `0`, or the step with index `1`.

**_`Return the minimum cost to reach the top of the floor`_**.

There is a robot on an `m x n` grid. The robot is initially located at the **_`top-left`_** corner (i.e., `grid[0][0]`). The robot tries to move to the **_`bottom-right`_** corner (i.e., `grid[m - 1][n - 1]`). The robot can only move either **_`down`_** or **_`right`_** at any point in time.

Given the two integers `m` and `n`, return **_the number of possible unique paths that the robot can take to reach the bottom-right corner_**.

The test cases are generated so that the answer will be less than or equal to `2 * 109`.

**Example 1**

```bash
Input: m = 3, n = 7
Output: 28
```

**Example 2**

```bash
Input: m = 3, n = 2
Output: 3
Explanation: From the top-left corner, there are a total of 3 ways to reach the bottom-right corner:
1. Right -> Down -> Down
2. Down -> Down -> Right
3. Down -> Right -> Down
```

### Constraints

- `1 <= m, n <= 100`

## Solution

**_`Recursive`_**

```cpp
#include<bits/stdc++.h>
using namespace std;
class Solution {
public:
     int countPaths(int i,int j,int n,int m)
        {
            if(i==(n-1)&&j==(m-1)) return 1;
            if(i>=n||j>=m) return 0;
            else return countPaths(i+1,j,n,m)+countPaths(i,j+1,n,m);
        }
        int uniquePaths(int m, int n) {
        return countPaths(0,0,m,n);
        }
    };
    int main()
    {
        Solution obj;
        int totalCount= obj.uniquePaths(3,7);
        cout<<"The total number of Unique Paths are "<<totalCount<<endl;
    }
```

**_`Dynamic Programming`_**

```cpp
#include<bits/stdc++.h>
using namespace std;
class Solution {
public:
    int countPaths(int i,int j,int n,int m, vector<vector<int>> &dp)
    {
        if(i==(n-1)&&j==(m-1)) return 1;
        if(i>=n||j>=m) return 0;
        if(dp[i][j]!=-1) return dp[i][j];
        else return dp[i][j]=countPaths(i+1,j,n,m,dp)+countPaths(i,j+1,n,m,dp);

    }

    int uniquePaths(int m, int n) {
        vector<vector<int>> dp(m+1,vector<int>(n+1,-1));

        //dp[1][1]=1;
        int num=countPaths(0,0,m,n,dp);
            if(m==1&&n==1)
                return num;
            return dp[0][0];
        }
    };

    int main()
    {
        Solution obj;
        int totalCount= obj.uniquePaths(3,7);
        cout<<"The total number of Unique Paths are "<<totalCount<<endl;
    }
```

**_`Dynamic Programming with Memoization`_**

```javascript
/**
 * @param {number} m
 * @param {number} n
 * @return {number}
 */
const mp = {};
var uniquePaths = function (m, n) {
  if (m === 0 || n === 0) return 0;
  if (m === 1 && n === 1) return 1;

  let key = m + "," + n;
  if (mp[key]) return mp[key];
  mp[key] = uniquePaths(m, n - 1) + uniquePaths(m - 1, n);
  return mp[key];
};
```
