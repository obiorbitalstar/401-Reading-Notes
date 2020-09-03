# Trees
A tree data structure can be defined recursively as a collection of nodes (starting at a root node), where each node is a data structure consisting of a value, together with a list of references to nodes (the "children"), with the constraints that no reference is duplicated, and none points to the root. 

## Common Terminology
* Node - A node is the individual item/data that makes up  the data structure
* Root - The root is the first/top Node in the tree

* Left Child - The node that is positioned to the left of  a root or node
* Right Child - The node that is positioned to the right  of a root or node
* Edge - The edge in a tree is the link between a parent  and child node
* Leaf - A leaf is a node that does not contain any * children
* Height - The height of a tree is determined by the * number of edges from the root to the bottommost node

## Traversals

### Depth First
Depth first traversal is where we prioritize going through the depth (height) of the tree first.

depth first search can be done in three ways 
* Pre-order 

    ```
    ALGORITHM preOrder(root)

    OUTPUT <-- root.value

     if root.left is not NULL
        preOrder(root.left)

     if root.right is not NULL
        preOrder(root.right)

    ```

* in-order 
    
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

* Post-order 
    
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

###  Breadth First
Breadth first traversal iterates through the tree by going through each level of the tree node-by-node

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
            

## Binary Trees

Binary trees restrict each node to have only 2 childern nodes ( left,right )

![img](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-15/resources/images/BinaryTree2.PNG)



## Big O
The Big O time complexity for inserting a new node is O(n). Searching for a specific node will also be O(n). Because of the lack of organizational structure in a Binary Tree, the worst case for most operations will involve traversing the entire tree. If we assume that a tree has n nodes, then in the worst case we will have to look at n items, hence the O(n) complexity.

The Big O space complexity for a node insertion using breadth first insertion will be O(w), where w is the largest width of the tree. For example, in the above tree, w is 4.

A “perfect” binary tree is one where every non-leaf node has exactly two children. The maximum width for a perfect binary tree, is 2^(h-1), where h is the height of the tree. Height can be calculated as log n, where n is the number of nodes.







code snippts resource: 

https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-15/resources/Trees.html