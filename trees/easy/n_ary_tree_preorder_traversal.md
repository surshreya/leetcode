
##  N-ary Tree Preorder Traversal

Given the ```root``` of an n-ary tree, return the ```preorder traversal``` of its nodes' values.

Nary-Tree input serialization is represented in their level order traversal. Each group of children is separated by the null value (See examples)

 
 


 

![narytreeexample](https://user-images.githubusercontent.com/118065908/233822113-57838a84-b8cb-4335-a1c1-e5473ef1ea25.png)



**Example 1**
```bash
Input: root = [1,null,3,2,4,null,5,6]
Output: [1,3,5,6,2,4]
```
![sample_4_964](https://user-images.githubusercontent.com/118065908/233822115-063951a2-1a9c-40fe-ba93-0d5a616bfc19.png)

**Example 2**
```bash
Input: root = [1,null,2,3,4,5,null,null,6,7,null,8,null,9,10,null,null,11,null,12,null,13,null,null,14]
Output: [1,2,3,6,7,11,14,4,8,12,5,9,13,10]
```

### Constraints

- ```The number of nodes in the tree is in the range [0, 104].```
- ```0 <= Node.val <= 104```
- ```The height of the n-ary tree is less than or equal to 1000.```

## Solution

```javascript
var preorder = function(root) {
    if(!root || root.length === 0) return [];
    const stack = [root];
    const traversed = [];

    while(stack.length > 0) {
        const current = stack.pop();
        traversed.push(current.val);
        for(let i = current.children.length - 1; i >= 0; i--) {
            stack.push(current.children[i]);
        }
    }
    return traversed;
};
```
