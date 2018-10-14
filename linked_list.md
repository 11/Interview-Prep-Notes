
### Iterating through a Linked List
Often times, interview questions will create a situation where you need to iterate through a Linked Lists in such a way that you need to create three separate conditions:

    - One for manipulating the head of the list
    - One for manipulating the middle of the list
    - One for manipulating the end of the list

All three of these situations have their subtitles, making each case unique.

### Purpose of this Post
The goal of this post is to have a one size fits all approach for the aforementioned conditions.


### How to Handle the Situation
A very common one size fits all approach is to use three nodes to iterate through a list: `tail`, a pointer used keeps track of the last node we touched;
`cur`, a pointer that keeps track of the current node we are performing operations on; and `front`, the next node we are going to interact with. By having
all three of these nodes, we can handle the aforementioned conditions - and even more general situations.


### Some Important Notes
The first thing to take note of is that I strongly suggest initializing `tail` to `null` - and or `None`; reason being that we can
iterate through a linked list with `cur` pointing to the first Node in the list, allowing for our loop to be consistently checking if
`cur` is `null` from the beginning, all the way to the end of the list. Also, something nice that comes out of setting `tail` to `null` is
that we have a clear way to check if we are on the first iteration in our loop, a condition that often requires it's own logic. (You'll
understand what I mean by this more as you try to linked list problems.)

Here is the section of code that pertains to initializing `tail` and using checking if you are on the <b>first</b> iteration:
```python
tail = None
cur = head
front = head.next

while cur is not None:
    # if on first iteration
    if tail is None:
        do_something()

    # other stuff here ...
```

Another thing to note is how we increment our pointers forward through the list. In order to properly increment everything forward,
you must increment starting with `tail`, and ending with `front`. Here is the logic
```python
while cur is not None:

    # loop logic up here

    # increment pointers
    tail = cur
    cur = None if front is None else front
    front = None if front.next is None else front.next
```


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
