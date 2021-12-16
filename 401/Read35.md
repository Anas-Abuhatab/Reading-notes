# Graphs

- graph: non-linear data structure that can be looked at as a collection of nodes potentially connected by line segments named edges.
- Some common terms:
  - Vertex: also called a “node”, this is a data object that can have zero or more adjacent vertices (or nodes). 
  - Edge: a connection between two nodes.
  - Neighbor: a node next to another, separated by an edge. 
  - Degree: number of edges connected to that vertex.
- Undirected graph: Each edge does not have a specific direction. There are no “directions” given to point to specific vertices.
- Directed graph: Each edge has a specific direction that it point to. 
- Complete graphs: when all nodes are connected to all other nodes. 
- Connected graphs: All nodes have at least one edge. A tree is a form of a connected graph!
- Disconnected graphs: Some nodes may not have edges.
- Acyclic graph: a directed graph without cycles. 
- Cycle: when a node can be traversed through and potentially end up back at itself. 
- Cyclic graph: A graph that has cycles. 
- Again, a cycle is a path of positive length that starts and ends with the same node. 
- Adjacency matrix: represented through a 2-dimensional array. 
  - Each row and column represent each node of the ds.
- Adjacency list: a collection of linked lists or array that lists all of the other nodes that are connected. 
- Weighted graph: graph with numbers assigned to the edges. These number are weights. 
#### Traversals 
- BreadthFirst: You start at a specific node. We need to create a visited set to keep track of nodes we have already traversed and to prevent going into cycles, causing infinite loop.
- Actual breadth first traversal definition: when you visit all nodes closest to the root, then keep traversing level by level. 
- Breadth first algo:
```
Enqueue the declared start node into the Queue.
Create a loop that will run while the node still has nodes present.
Dequeue the first node from the queue
if the Dequeue‘d node has unvisited child nodes, add the unvisited children to visited set and insert them into the queue.
```
- Pseudo code for breadth first:
```
ALGORITHM BreadthFirst(vertex)
    DECLARE nodes <-- new List()
    DECLARE breadth <-- new Queue()
    DECLARE visited <-- new Set()

    breadth.Enqueue(vertex)
    visited.Add(vertex)

    while (breadth is not empty)
        DECLARE front <-- breadth.Dequeue()
        nodes.Add(front)

        for each child in front.Children
            if(child is not visited)
                visited.Add(child)
                breadth.Enqueue(child)   

    return nodes;
```
- Depth first traversal algo:
```
Push the root node into the stack
Start a while loop while the stack is not empty
Peek at the top node in the stack
If the top node has unvisited children, mark the top node as visited, and then Push any unvisited children back into the stack.
If the top node does not have any unvisited children, Pop that node off the stack
repeat until the stack is empty.
```
- Real word uses for graphs:
  - GPS and Mapping
  - Driving Directions
  - Social Networks
  - Airline Traffic
  - Netflix uses graphs for suggestions of products
  