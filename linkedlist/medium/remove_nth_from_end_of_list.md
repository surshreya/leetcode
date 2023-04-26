
##   Remove Nth Node From End of List

Given the ```head``` of a linked list, remove the ```nth``` node from the ```end of the list``` and return its ```head```.

 
 


 

![remove_ex1](https://user-images.githubusercontent.com/118065908/234664519-40294988-28dd-42ea-8c03-bc12a4f16627.jpg)



**Example 1**
```bash
Input: head = [1,2,3,4,5], n = 2
Output: [1,2,3,5]
```

**Example 2**
```bash
Input: head = [1], n = 1
Output: []
```

**Example 3**
```bash
Input: head = [1,2], n = 1
Output: [1]
```

### Constraints

- ```The number of nodes in the list is sz.```
- ```1 <= sz <= 30```
- ```0 <= Node.val <= 100```
- ```1 <= n <= sz```

## Solution

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} head
 * @param {number} n
 * @return {ListNode}
 */
var removeNthFromEnd = function(head, n) {
    const start = new ListNode();
    start.next = head;

    let p = start;
    let q = start;

    for(let i=1;i<=n;i++) {
        p=p.next;
    }

    while(p.next) {
        p=p.next;
        q=q.next;
    }

    q.next = q.next.next;

    return start.next;
};
```
