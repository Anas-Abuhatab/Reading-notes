# Implementation: Stacks and Queues

## Stacks and Queues

#### Stacks

- A stack is a data structure that consists of Nodes
- Terms for stack:
  1. Push - Nodes or items that are put into the stack are pushed
  2. Pop - Nodes or items that are removed from the stack are popped. When you attempt to pop an empty stack an exception will be raised. 
  3. Top - This is the top of the stack.
  4. Peek - When you peek you will view the value of the top Node in the stack. When you attempt to peek an empty stack an exception will be raised.
  5. IsEmpty - returns true when stack is empty otherwise returns false.
- Stacks follow these concepts:
  1. FILO: First In Last Out
  2. LIFO: Last In First Out
- pseudocode to push a value onto a stack:
```
ALOGORITHM push(value)
// INPUT <-- value to add, wrapped in Node internally
// OUTPUT <-- none
   node = new Node(value)
   node.next <-- Top
   top <-- Node
```
- Popping a Node off a stack is the action of removing a Node from the top.
- pseudocode for a peek
```
ALGORITHM peek()
// INPUT <-- none
// OUTPUT <-- value of top Node in stack
// EXCEPTION if stack is empty

   return top.value
```
- pseudocode for isEmpty
```
ALGORITHM isEmpty()
// INPUT <-- none
// OUTPUT <-- boolean

return top = NULL
```

#### Queue

- Terminology for a queue is
  1. Enqueue - Nodes or items that are added to the queue.
  2. Dequeue - Nodes or items that are removed from the queue. If called when the queue is empty an exception will be raised.
  3. Front - This is the front/first Node of the queue.
  4. Rear - This is the rear/last Node of the queue.
  5. Peek - When you peek you will view the value of the front Node in the queue. If called when the queue is empty an exception will be raised.
  6. IsEmpty - returns true when queue is empty otherwise returns false.
- Queues follow these concepts:
  1. FIFO: First in First Out
  2. LILO: Last in Last Out
- pseudocode for the enqueue method:
```
ALGORITHM enqueue(value)
// INPUT <-- value to add to queue (will be wrapped in Node internally)
// OUTPUT <-- none
   node = new Node(value)
   rear.next <-- node
   rear <-- node
```
- pseudocode for the dequeue method:
```
ALGORITHM dequeue()
// INPUT <-- none
// OUTPUT <-- value of the removed Node
// EXCEPTION if queue is empty

   Node temp <-- front
   front <-- front.next
   temp.next <-- null

   return temp.value
```
- pseudocode for a peek:
```
ALGORITHM peek()
// INPUT <-- none
// OUTPUT <-- value of the front Node in Queue
// EXCEPTION if Queue is empty

   return front.value
```