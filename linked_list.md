
### Iterating through a Linked List
Often times, interview questions will create a situation where you need to iterate through a Linked Lists in such a way that you need to create three separate conditions:

    - One for manipulating the head of the list
    - One for manipulating the middle of the list
    - One for manipulating the end of the list

All three of these situations have their subtitles, making each case unique.

The goal of this post is to have a one size fits all approach for the aforementioned conditions.


### How to handle the situation
A very common one size fits all approach is to use three nodes to iterate through a list: `tail`, a pointer that keeps track of the last node we touched;
`cur` a pointer that keeps track of the current node we are working with; and `front`, the next node we are going to interact with. By having all three of these nodes,
we can handle of the above conditions.

### The Code

```python
# Node class
class Node:
    def __init__(self, val, next=None):
        self.val = val
        self.next = next

# imagine the create_list function existed, and returned a linked list
# head = a -> b -> c -> d -> e -> None
head = create_list()

tail = None
cur = head
front = cur.next

while cur is not None:

    # handle logic
    if tail is None:
        handle_front_of_list()
    elif front is None:
        handle_end_of_list()
    else:
        handle_middle_of_list()


    # update pointers
    tail = cur
    cur = None if front is None else front
    front = None if front.next is None else front.next
```
