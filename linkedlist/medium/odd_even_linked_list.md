
##   Odd Even Linked List

Given the ```head``` of a singly linked list, group all the nodes with odd indices together followed by the nodes with even indices, and return the ```reordered list```.

The ***```first```*** node is considered ***```odd```***, and the ***```second```*** node is ```even```, and so on.

Note that the relative order inside both the even and odd groups should remain as it was in the input.

***```You must solve the problem in O(1) extra space complexity and O(n) time complexity.```***
 


 


 

![oddeven-linked-list](https://user-images.githubusercontent.com/118065908/235077222-47a83e85-d2f2-4ffc-954d-c709e6d2a0bc.jpg)



**Example 1**
```bash
Input: head = [1,2,3,4,5]
Output: [1,3,5,2,4]
```
![oddeven2-linked-list](https://user-images.githubusercontent.com/118065908/235077234-2cfe3e19-582b-46a2-b3ca-d3ef8c887b28.jpg)

**Example 2**
```bash
Input: head = [2,1,3,5,6,4,7]
Output: [2,3,6,7,1,5,4]
```

### Constraints

- ```The number of nodes in the linked list is in the range [0, 104].```
- ```-106 <= Node.val <= 106```

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
     * @return {ListNode}
     */
    var oddEvenList = function(head) {
        if(!head) return head;

        let odd_list = new ListNode();
        let odd = odd_list;
        let even_list = new ListNode();
        let even = even_list;

        let temp = head;
        let i = 1;
        while(temp) {
            if(i%2 === 0) {
                even.next = temp;
                even = even.next;
            } else {
                odd.next = temp;
                odd = odd.next;
            }
            temp=temp.next;
            i++;
        }

        odd.next = even_list.next;
        even.next = null;
        return odd_list.next;
    };
```
