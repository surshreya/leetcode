## Binary Tree Inorder Traversal

Given the root of a binary tree, return the inorder traversal of its nodes' values.

**Example 1**

```bash
Input: root = [1,null,2,3]
Output: [1,3,2]
```

**Example 2**

```bash
Input: root = []
Output: []
```

**Example 3**

```bash
Input: root = [1]
Output: [1]
```

### Constraints

- `The number of nodes in the tree is in the range [0, 100].`
- `-100 <= Node.val <= 100`

## Solution

```javascript
const inorderTraversalR = (root, inorder) => {
  if (!root) {
    return;
  }
  inorderTraversalR(root.left, inorder);
  inorder.push(root.val);
  inorderTraversalR(root.right, inorder);
};
var inorderTraversal = function (root) {
  let inorder = [];
  inorderTraversalR(root, inorder);
  return inorder;
};
```
