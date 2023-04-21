
##  Reverse Linked List

Given the head of a singly linked list, reverse the list, and return the reversed list.
 

 


 




**Example 1**
```bash
Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]
```
**Example 2**
```bash
Input: head = [1,2]
Output: [2,1]
```
**Example 3**
```bash
Input: head = []
Output: []
```

### Constraints

- ```The number of nodes in the list is the range [0, 5000].```
- ```-5000 <= Node.val <= 5000```

    
## Solution

```javascript
var reverseList = function(head) {
    if(!head || !head.next) return head;

    let p = head, q = null, r = null;
    while(p) {
        r=q;
        q=p;
        p=p.next;
        q.next=r;
    }
    return q;
};
```
