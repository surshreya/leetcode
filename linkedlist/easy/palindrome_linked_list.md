
##   Palindrome Linked List

Given the head of a singly linked list, return ```true``` if it is a **palindrome** or ```false``` otherwise.
 
 

 


 ![pal1linked-list](https://user-images.githubusercontent.com/118065908/233565184-9378c0c6-4d2f-4e7c-96ac-816fcf4023dc.jpg)





**Example 1**
```bash
Input: head = [1,2,2,1]
Output: true
```
**Example 2**
```bash
Input: head = [1,2]
Output: false
```

### Constraints

- ```The number of nodes in the list is in the range [1, 105].```
- ```0 <= Node.val <= 9```


## Solution

```javascript
const Reverse = head => {
     let p = head, q = null, r = null;
     while(p) {
         r=q;
         q=p;
         p=p.next;
         q.next=r;
     } 
     head = q;
     return head;
 }
var isPalindrome = function(head) {
    if(!head && !head.next) return true;

    let p = head, q = head;
    while(p.next && p.next.next) {
        p=p.next.next;
        q=q.next;
    }

    q.next = Reverse(q.next);
    q=q.next;

    let r = head;
    while(q) {
        if(q.val !== r.val) {
            return false;
        }
        q=q.next;
        r=r.next;
    }

    return true;
};
```
