## Flood Fill

An image is represented by an `m x n` integer grid `image` where `image[i][j]` represents the pixel value of the image.

You are also given three integers **_`sr, sc, and color`_**. You should perform a **flood fill** on the image starting from the pixel **_`image[sr][sc]`_**.

To perform a **flood fill**, consider the starting pixel, plus any pixels **connected 4-directionally** to the starting pixel of the same color as the starting pixel, plus any pixels connected **4-directionally** to those pixels **_`(also with the same color)`_**, and so on. Replace the color of all of the aforementioned pixels with color.

`Return the modified image after performing the flood fill`.

![flood1-grid](https://user-images.githubusercontent.com/118065908/234639879-df42c70e-cd4f-4899-9bac-b8a75f5d19e5.jpg)
**Example 1**

```bash
Input: image = [[1,1,1],[1,1,0],[1,0,1]], sr = 1, sc = 1, color = 2
Output: [[2,2,2],[2,2,0],[2,0,1]]
Explanation: From the center of the image with position (sr, sc) = (1, 1) (i.e., the red pixel), all pixels connected by a path of the same color as the starting pixel (i.e., the blue pixels) are colored with the new color.
Note the bottom corner is not colored 2, because it is not 4-directionally connected to the starting pixel.
```

**Example 2**

```bash
Input: image = [[0,0,0],[0,0,0]], sr = 0, sc = 0, color = 0
Output: [[0,0,0],[0,0,0]]
Explanation: The starting pixel is already colored 0, so no changes are made to the image.
```

### Constraints

- `m == image.length`
- `n == image[i].length`
- `1 <= m, n <= 50`
- `0 <= image[i][j], color < 2^16`
- `0 <= sr < m`
- `0 <= sc < n`

## Solution

**_Recursive_**

```javascript
/**
 * @param {number[][]} image
 * @param {number} sr
 * @param {number} sc
 * @param {number} color
 * @return {number[][]}
 */

const explore = (image, r, c, source, visited, color) => {
  const validRow = r >= 0 && r < image.length;
  const validCol = c >= 0 && c < image[0].length;

  if (!validRow || !validCol) return;
  if (image[r][c] !== source) return;

  const pos = r + "," + c;
  if (visited.has(pos)) return;

  visited.add(pos);
  image[r][c] = color;
  explore(image, r - 1, c, source, visited, color);
  explore(image, r + 1, c, source, visited, color);
  explore(image, r, c - 1, source, visited, color);
  explore(image, r, c + 1, source, visited, color);
};
var floodFill = function (image, sr, sc, color) {
  const visited = new Set();
  const source = image[sr][sc];
  explore(image, sr, sc, source, visited, color);
  return image;
};
```
