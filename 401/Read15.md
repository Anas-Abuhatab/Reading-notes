# Trees

**Common Terminology:**  
- node: individual item/data that makes up the data structure
- Root: The root is the first/top Node in the tree
- Left Child: The node that is positioned to the left of a root or node
- Right Child: The node that is positioned to the right of a root or node
- Edge: The edge in a tree is the link between a parent and child node
- Leaf: A leaf is a node that does not contain any children
- Height: The height of a tree is determined by the number of edges from the root to the bottommost node  

**Traversals:**  
- Depth first:  prioritize going through the depth (height) of the tree first. Three methods:
  1. Pre-order: root >> left >> right
  2. In-order: left >> root >> right
  3. Post-order: left >> right >> root

- The most common way to traverse through a tree is to use recursion.

- pre-order traversal:
```
ALGORITHM preOrder(root)

  OUTPUT <-- root.value

  if root.left is not NULL
      preOrder(root.left)

  if root.right is not NULL
      preOrder(root.right)
```
- Pre-order means that the root has to be looked at first. 
- In-order:
```
ALGORITHM inOrder(root)
// INPUT <-- root node
// OUTPUT <-- in-order output of tree node's values

    if root.left is not NULL
        inOrder(root.left)

    OUTPUT <-- root.value

    if root.right is not NULL
        inOrder(root.right)
```
- Post order:
```
ALGORITHM postOrder(root)
// INPUT <-- root node
// OUTPUT <-- post-order output of tree node's values

    if root.left is not NULL
        postOrder(root.left)

    if root.right is not NULL
        postOrder(root.right)

    OUTPUT <-- root.value
```
- The biggest difference between each of the traversals is when you are looking at the root node.
- Breadth first traversal iterates through the tree by going through each level of the tree node-by-node.
- utilizing a built-in queue to implement a breadth first traversal:
```
ALGORITHM breadthFirst(root)
// INPUT  <-- root node
// OUTPUT <-- front node of queue to console

  Queue breadth <-- new Queue()
  breadth.enqueue(root)

  while breadth.peek()
    node front = breadth.dequeue()
    OUTPUT <-- front.value

    if front.left is not NULL
      breadth.enqueue(front.left)

    if front.right is not NULL
      breadth.enqueue(front.right)
```
- no structural rules for where nodes are “supposed to go” in a binary tree. it really doesn’t matter where a new node gets placed.
- The Big O time complexity for inserting a new node is O(n).
- The Big O space complexity for a node insertion using breadth first insertion will be O(w) (w is the largest width of tree). 
- maximum width for a perfect binary tree, is 2^(h-1), where h is the height of the tree.
- A Binary Search Tree (BST) is a type of tree that does have some structure attached to it.
- The best way to approach a BST search is with a while loop.
- The Big O time complexity of a Binary Search Tree’s insertion and search operations is O(h), or O(height).
- The Big O space complexity of a BST search would be O(1). During a search, we are not allocating any additional space.