# Linked Lists

## Linked Lists
- Each Node references the next Node in the link.
- Two tpes of linked lists: Singly and Doubly
- Linked List: A data structure that contains nodes that links/points to the next node in the list.
- Nodes: the individual items/links that live in a linked list. Each node contains the data for each link.
- Head: reference type of type Node to the first node in a linked list.
- While traversing a linked list, you are not able to use a foreach or for loop.
- The best way to approach a traversal is through the use of a while() loop.
- If we accidentally end up trying to traverse on a node that is null, a NullReferenceException gets thrown and our program will crash/end.
- Pseudo code for an includes:
```
ALGORTIHM Includes (value)
		// INPUT <-- integer value
		// OUTPUT <-- boolean
			
			Current <-- Head

			WHILE Current is not NULL
				IF Current.Value is equal to value
					return TRUE

				Current <-- Current.Next

			return FALSE
```
- Big O of time for Includes would be O(n). This is because, at its worse case, the node we are looking for will be the very last node in the linked list. n represents the number of nodes in the linked list.
- Big O of space for Includes would be O(1). This is because there is no additional space being used than what is already given to us with the linked list input.
- Pseudo code for an Add method on a Linked list:
```
ALGORITHM Add(newNode)
		// INPUT <-- Node to add 
		// OUTPUT<-- No output

			Current <-- Head
			newNode.Next <-- Head
			Head <-- newNode
			Current <-- Head
 ```
 - IMPORTANT: Regardless of the number of Nodes that this linked list has, it will always be a O(1) time and space because it takes the same amount of time to add a new node to the beginning of the list, and no additional resources are being used.
 - Pseudo code for an AddBefore method in a linked list:
```
ALGORITHM AddBefore(newNode, existingNode)
		// INPUT <-- New Node, Existing Node
		// OUTPUT <-- No Output

			Current <-- Head

			while Current.Next is not equal to NULL
				if Current.Next.Value is equal to existingNode.Value
					newNode.Next <-- existingNode
					Current.Next <-- newNode

				Current <-- Current.Next;		
```
- Time efficiency for this example: O(n) because we could be inserting the new node, worst case scenario, at the end. With n being the number of nodes possible, we would therefore have O(n) time efficiency.
- Space efficiency for this example: O(1) because, like before, no additional space is being used allocated outside of what is given to us on the input.
- Pseudo code for a method to print out all nodes in a linked list:
```
ALGORITHM Print()
		// INPUT <-- None
		// OUTPUT <-- string to console

			Current <-- Head

			while Current.Next is not equal to NULL
				OUTPUT <-- "Current.Value --> "
				Current <-- Current.Next

			OUTPUT <-- "Current.Value --> NULL"
```
## What’s a Linked List, Anyway pt1
- One characteristic of linked lists is that they are linear data structures, which means that there is a sequence and an order to how they are constructed and traversed.
- In non-linear data structures, items don’t have to be arranged in order, which means that we could traverse the data structure non-sequentially.
- Both arrays and linked lists are linear data structures (order matters for both of them). 
- The biggest differentiator between arrays and linked lists is the way that they use memory in our machines. 
- Abstraction isn’t magic, it’s just the simplicity of hiding away things that you don’t need to see or deal with all of the time.
- When an array is created, it needs a certain amount of memory. If we had 7 letters that we needed to store in an array, we would need 7 bytes of memory to represent that array. 
- Linked lists don’t need to take up a single block of memory; instead, the memory that they use can be scattered throughout.
- The fundamental difference between arrays and linked lists is that arrays are static data structures, while linked lists are dynamic data structures.
- A single node contains two parts: data, or the information that the node contains, and a reference to the next node.
- "A node only knows about what data it contains, and who its neighbor is."




## What’s a Linked List, Anyway pt2
- Hard part about linked lists: logic that goes into deciding when and whether or not to use them that’s hard to wrap your head around.
- Big O Notation is a way of evaluating the performance of an algorithm.
- There are two major points to consider when thinking about how an algorithm performs: how much time it requires at runtime given how much time and memory it needs.
- One way to think about Big O notation is a way to express the amount of time that a function, action, or algorithm takes to run based on how many elements we pass to that function.
- Big O Notation takes into account: the speed and efficiency with which something functions when its input grows to be any (crazy big!) size.
- An O(1) function takes constant time, which is to say that it doesn’t matter how many elements we have, or how huge our input is: it’ll always take the same amount of time and memory to run our algorithm.
- An O(n) function is linear, which means that as our input grows (from ten numbers, to ten thousand, to ten million), the space and time that we need to run that algorithm grows linearly.
- O(n²) function clearly takes exponentially more time and memory the more elements that you have.
- "a linked list is usually efficient when it comes to adding and removing most elements, but can be very slow to search and find a single element."
