# Stack

{% page-ref page="stack-continued.md" %}

{% tabs %} {% tab title="Stack.py" %}

```python
# lets look at the idea of another data structure
# a Stack like a stack of plates or books
# LIFO (last in first out)

# we can push items on to the stack
# we can pop items off a stack
# and we can peek at the item at the top of the stack

# think of how you could utilise a linked list to form a stack

"""
A stack is a data structure whose primary purpose is to store and
return elements in Last In First Out order.
1. Implement the Stack class using an array as the underlying storage structure.
   Make sure the Stack tests pass.
2. Re-implement the Stack class, this time using the linked list implementation
   as the underlying storage structure.
   Make sure the Stack tests pass.
3. What is the difference between using an array vs. a linked list when
   implementing a Stack?
"""

# Implement a Stack using an array for the underlying storage
class StackA:
    def __init__(self):
        self.storage = []

    def __len__(self):
        return len(self.storage)

    def push(self, value):
        self.storage.append(value)

    def pop(self):
        if len(self.storage) == 0:
            return None
        return self.storage.pop()



from linked_list import LinkedList

# Stack implementation using a Linked List
class StackL:
    def __init__(self):
        self.size = 0
        self.storage = LinkedList()

    def __len__(self):
        return self.size

    def push(self, value):
        self.storage.add_to_head(value)
        self.size += 1

    def pop(self):
        if self.size == 0:
            return None
        self.size -= 1
        return self.storage.remove_head()
```

{% endtab %}

{% tab title="Stack2.py" %}

```python
# lets look at the idea of another data structure
# a Stack like a stack of plates or books
# LIFO (last in first out)

# we can push items on to the stack
# we can pop items off a stack
# and we can peek at the item at the top of the stack

# think of how you could utilise a linked list to form a stack

"""
A stack is a data structure whose primary purpose is to store and
return elements in Last In First Out order.
1. Implement the Stack class using an array as the underlying storage structure.
   Make sure the Stack tests pass.
2. Re-implement the Stack class, this time using the linked list implementation
   as the underlying storage structure.
   Make sure the Stack tests pass.
3. What is the difference between using an array vs. a linked list when
   implementing a Stack?
"""

# Implement a Stack using an array for the underlying storage
class StackA:
    def __init__(self):
        self.storage = []

    def __len__(self):
        return len(self.storage)

    def push(self, value):
        self.storage.append(value)

    def pop(self):
        if len(self.storage) == 0:
            return None
        return self.storage.pop()

    def peek(self):
        return self.storage[-1]



from linked_list import LinkedList

# Stack implementation using a Linked List
class StackL:
    def __init__(self):
        self.size = 0
        self.storage = LinkedList()

    def __len__(self):
        return self.size

    def push(self, value):
        self.storage.add_to_head(value)
        self.size += 1

    def pop(self):
        if self.size == 0:
            return None
        self.size -= 1
        return self.storage.remove_head()

    def peek(self):
        return self.storage.head.get_value()


```

{% endtab %} {% endtabs %}

```python
# LIFO: last in first out

# create the abstract data type
class Stack:

    def __init__(self):
        # initialize it to a one dimensional array or linked list
        self.stack = []

    """
    Stack methods (push, pop, peek, is_empty, stack_size)
    """

    # function for adding item into the stack O(1)
    def push(self, data):
        self.stack.append(data)

    # function for removing last item inserted O(1)
    def pop(self):

        # first check to make sure its not an empty stack
        if self.stack_size() < 1:
            return -1

        # get the last item in the stack
        data = self.stack[-1]
        # remove it
        del self.stack[-1]
        # return the data
        return data

    # function to return the last item in the stack without removing it O(1)
    def peek(self):
        return self.stack[-1]

    # function to check if the stack is empty O(1)
    def is_empty(self):
        return self.stack == []

    # function to return the size of the stack O(1)
    def stack_size(self):
        return len(self.stack)


"""
Using the methods
"""
stack = Stack()
stack.push(1)
stack.push(2)
stack.push(3)
print(f'Size: {stack.stack_size()}')
print(f'Popped item: {stack.pop()}')
print(f'Size: {stack.stack_size()}')
print(f'Peeked item: {stack.peek()}')
print(f'Size: {stack.stack_size()}')

```

## Stack

- Implementation of an interpreter for a small language that does multiplication/addition/etc.
- Design a `MinStack` data structure that supports a `min()` operation that returns the minimum value in the stack in O\(1\) time.
- Write an algorithm to determine if all of the delimiters in an expression are matched and closed.
  - E.g. `{ac[bb]}`, `[dklf(df(kl))d]{}` and `{[[[]]]}` are matched. But `{3234[fd` and `{df][d}` are not.
  - [Source](http://blog.gainlo.co/index.php/2016/09/30/uber-interview-question-delimiter-matching/)
- Sort a stack in ascending order using an additional stack.

### Stacks in Python

[Stacks](https://www.educative.io/blog/data-structures-stack-queue-java-tutorial) are a sequential data structure that act as the Last-in, First-out \(LIFO\) version of queues. The last element inserted in a stack is considered at the **top of the stack** and is the only accessible element. To access a middle element, you must first remove enough elements to make the desired element the top of the stack.

Many developers imagine stacks as a stack of dinner plates; you can add or remove plates to the top of the stack but must move the whole stack to place one at the bottom.

Adding elements is known as a **push,** and removing elements is known as a **pop**. You can implement stacks in Python using the built-in list structure. With list implementation, push operations use the `append()` method, and pop operations use `pop()`.

{% tabs %} {% tab title="Stack Python" %}

```python
stack = []

# append() function to push
# element in the stack
stack.append('a')
stack.append('b')
stack.append('c')

print('Initial stack')
print(stack)

# pop() function to pop
# element from stack in
# LIFO order
print('\nElements popped from stack:')
print(stack.pop())
print(stack.pop())
print(stack.pop())

print('\nStack after elements are popped:')
print(stack)

```

##

{% endtab %}

{% tab title="Stack Javascript" %}

```javascript
//creates a stack
let stack = function () {
  //two variables of the stack
  this.count = 0; //keeps track of the count of the stack
  this.storage = {}; //empty object

  //adding the  value on to the end of the stack
  this.push = function (value) {
    this.storage[this.count] = value;
    this.count++;
  };

  //removes and returns the value at the end of the stack
  this.pop = function () {
    if (this.count === 0) {
      return undefined;
    }
    this.count--;
    const result = this.storage[this.count];
    //removes the top element and returns it
    delete this.storage[this.count];
    return result;
  };

  //to know the size of the stack
  this.size = function () {
    return this.count;
  };

  //peek() - returns the value top of the stack i.e which is at the end of the stack
  this.peek = function () {
    return this.storage[this.count - 1];
  };
};
let myStack = new stack();

myStack.push(1);
myStack.push(2);
console.log(myStack.peek());
console.log(myStack.pop());
console.log(myStack.peek());
```

{% endtab %} {% endtabs %}

**Advantages:**

- Offers LIFO data management that’s impossible with arrays
- Automatic scaling and object cleanup
- Simple and reliable data storage system

**Disadvantages:**

- Stack memory is limited
- Too many objects on the stack leads to a stack overflow error

**Applications:**

- Used for making highly reactive systems
- Memory management systems use stacks to handle the most recent requests first
- Helpful for questions like parenthesis matching

#### Common stacks interview questions in Python

- Implement a queue using stacks
- Evaluate a Postfix expression with a stack
- Next greatest element using a stack
- Create a `min()` function using a stack

## Stack in Python

> A Computer Science portal for geeks. It contains well written, well thought and well explained computer science and programming articles, quizzes and practice/competitive programming/company interview Questions.

A stack is a linear data structure that stores items in a Last-In/First-Out \(LIFO\) or First-In/Last-Out \(FILO\) manner. In stack, a new element is added at one end and an element is removed from that end only. The insert and delete operations are often called push and pop.

The functions associated with stack are:

- **empty\(\)** – Returns whether the stack is empty – Time Complexity: O\(1\)
- **size\(\)** – Returns the size of the stack – Time Complexity: O\(1\)
- **top\(\)** – Returns a reference to the topmost element of the stack – Time Complexity: O\(1\)
- **push\(a\)** – Inserts the element ‘a’ at the top of the stack – Time Complexity: O\(1\)
- **pop\(\)** – Deletes the topmost element of the stack – Time Complexity: O\(1\)

### Implementation

There are various ways from which a stack can be implemented in Python. This article covers the implementation of a stack using data structures and modules from the Python library.  
Stack in Python can be implemented using the following ways:

- list
- Collections.deque
- queue.LifoQueue

#### Implementation using list:

Python’s built-in data structure list can be used as a stack. Instead of push\(\), append\(\) is used to add elements to the top of the stack while pop\(\) removes the element in LIFO order.  
Unfortunately, the list has a few shortcomings. The biggest issue is that it can run into speed issues as it grows. The items in the list are stored next to each other in memory, if the stack grows bigger than the block of memory that currently holds it, then Python needs to do some memory allocations. This can lead to some append\(\) calls taking much longer than other ones.

- Python3

```python
# Python program to
# demonstrate stack implementation
# using list


stack = []

# append() function to push
# element in the stack
stack.append('a')
stack.append('b')
stack.append('c')

print('Initial stack')
print(stack)

# pop() function to pop
# element from stack in
# LIFO order
print('\nElements popped from stack:')
print(stack.pop())
print(stack.pop())
print(stack.pop())

print('\nStack after elements are popped:')
print(stack)

# uncommenting print(stack.pop())
# will cause an IndexError
# as the stack is now empty

```

**Output:**

Initial stack \['a', 'b', 'c'\]

Elements popped from stack: c b a

Stack after elements are popped: \[\]

Traceback \(most recent call last\): File "/home/2426bc32be6a59881fde0eec91247623.py", line 25, in print\(stack.pop\(\)\)  
IndexError: pop from empty list

#### Implementation using collections.deque:

Python stack can be implemented using the deque class from the collections module. Deque is preferred over the list in the cases where we need quicker append and pop operations from both the ends of the container, as deque provides an O\(1\) time complexity for append and pop operations as compared to list which provides O\(n\) time complexity.  
The same methods on deque as seen in the list are used, append\(\) and pop\(\).

- Python3

```python
# Python program to
# demonstrate stack implementation
# using collections.deque


from Collections import deque

stack = deque()

# append() function to push
# element in the stack
stack.append('a')
stack.append('b')
stack.append('c')

print('Initial stack:')
print(stack)

# pop() function to pop
# element from stack in
# LIFO order
print('\nElements popped from stack:')
print(stack.pop())
print(stack.pop())
print(stack.pop())

print('\nStack after elements are popped:')
print(stack)

# uncommenting print(stack.pop())
# will cause an IndexError
# as the stack is now empty
```

**Output:**

Initial stack: deque\(\['a', 'b', 'c'\]\)

Elements popped from stack: c b a

Stack after elements are popped: deque\(\[\]\)

Traceback \(most recent call last\): File "/home/97171a8f6fead6988ea96f86e4b01c32.py", line 29, in print\(stack.pop\(\)\)  
IndexError: pop from an empty deque

#### Implementation using queue module

Queue module also has a LIFO Queue, which is basically a Stack. Data is inserted into Queue using the put\(\) function and get\(\) takes data out from the Queue.

There are various functions available in this module:

- **maxsize** – Number of items allowed in the queue.
- **empty\(\)** – Return True if the queue is empty, False otherwise.
- **full\(\)** – Return True if there are _maxsize_ items in the queue. If the queue was initialized with maxsize=0 \(the default\), then full\(\) never returns True.
- **get\(\)** – Remove and return an item from the queue. If the queue is empty, wait until an item is available.
- **get_nowait\(\)** – Return an item if one is immediately available, else raise QueueEmpty.
- **put\(item\)** – Put an item into the queue. If the queue is full, wait until a free slot is available before adding the item.
- **put_nowait\(item\)** – Put an item into the queue without blocking.
- **qsize\(\)** – Return the number of items in the queue. If no free slot is immediately available, raise QueueFull.
- Python3

### Python3

\`\`

\`\`

\`\`

```python
# Python program to
# demonstrate stack implementation
# using queue module


from queue import LifoQueue

# Initializing a stack
stack = LifoQueue(maxsize = 3)

# qsize() show the number of elements
# in the stack
print(stack.qsize())

# put() function to push
# element in the stack
stack.put('a')
stack.put('b')
stack.put('c')

print("Full: ", stack.full())
print("Size: ", stack.qsize())

# get() function to pop
# element from stack in
# LIFO order
print('\nElements popped from the stack')
print(stack.get())
print(stack.get())
print(stack.get())

print("\nEmpty: ", stack.empty())
```

**Output:**

0 Full: True Size: 3

Elements popped from the stack c b a

Empty: True

#### Implementation using singly linked list:

The linked list has two methods addHead\(item\) and removeHead\(\) that run in constant time. These two methods are suitable to implement a stack.

- **getSize\(\)**– Get the number of items in the stack.
- **isEmpty\(\)** – Return True if the stack is empty, False otherwise.
- **peek\(\)** – Return the top item in the stack. If the stack is empty, raise an exception.
- **push\(value\)** – Push a value into the head of the stack.
- **pop\(\)** – Remove and return a value in the head of the stack. If the stack is empty, raise an exception.

Below is the implementation of the above approach:

- Python3

```python
# Python program to demonstrate
# stack implementation using a linked list.
# node class
class Node:
   def __init__(self, value):
      self.value = value
      self.next = None

class Stack:

   # Initializing a stack.
   # Use a dummy node, which is
   # easier for handling edge cases.
   def __init__(self):
      self.head = Node("head")
      self.size = 0

   # String representation of the stack
   def __str__(self):
      cur = self.head.next
      out = ""
      while cur:
         out += str(cur.value) + "->"
         cur = cur.next
      return out[:-3]

   # Get the current size of the stack
   def getSize(self):
      return self.size

   # Check if the stack is empty
   def isEmpty(self):
      return self.size == 0

   # Get the top item of the stack
   def peek(self):

      # Sanitary check to see if we
      # are peeking an empty stack.
      if self.isEmpty():
         raise Exception("Peeking from an empty stack")
      return self.head.next.value

   # Push a value into the stack.
   def push(self, value):
      node = Node(value)
      node.next = self.head.next
      self.head.next = node
      self.size += 1

   # Remove a value from the stack and return.
   def pop(self):
      if self.isEmpty():
         raise Exception("Popping from an empty stack")
      remove = self.head.next
      self.head.next = self.head.next.next
      self.size -= 1
      return remove.value

# Driver Code
if __name__ == "__main__":
   stack = Stack()
   for i in range(1, 11):
      stack.push(i)
   print(f"Stack: {stack}")

   for _ in range(1, 6):
      remove = stack.pop()
      print(f"Pop: {remove}")
   print(f"Stack: {stack}")
```

**Output:**

Stack: 10 -&gt; 9 -&gt; 8 -&gt; 7 -&gt; 6 -&gt; 5 -&gt; 4 -&gt; 3 -&gt; 2 -&gt; 1

Pop: 10 Pop: 9 Pop: 8 Pop: 7 Pop: 6

Stack: 5 -&gt; 4 -&gt; 3 -&gt; 2 -&gt; 1

```python

# Python program to
# demonstrate stack implementation
# using list


stack = []

# append() function to push
# element in the stack
stack.append('a')
stack.append('b')
stack.append('c')

print('Initial stack')
print(stack)

# pop() function to pop
# element from stack in
# LIFO order
print('\nElements popped from stack:')
print(stack.pop())
print(stack.pop())
print(stack.pop())

print('\nStack after elements are popped:')
print(stack)

# uncommenting print(stack.pop())
# will cause an IndexError
# as the stack is now empty
```

{% page-ref page="../array/" %}

{% page-ref page="../binary-search-tree/" %}

{% page-ref page="../untitled-4/" %}

{% page-ref page="../array/extra-array.md" %}

{% page-ref page="./" %}

{% page-ref page="../binary-tree/" %}

{% page-ref page="../untitled-6/" %}

{% page-ref page="../untitled-5/" %}

{% page-ref page="../untitled-2/" %}

{% page-ref page="../untitled-3/" %}

{% page-ref page="../queue/queue-sandbox.md" %}

{% page-ref page="../untitled-5/" %}

{% page-ref page="../untitled-4/double-linked-list.md" %}

{% page-ref page="../untitled-1/" %}

{% page-ref page="../untitled/" %}

{% page-ref page="../heap/" %}
