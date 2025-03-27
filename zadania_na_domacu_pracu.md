# Binary Search Tree Implementation Assignment 

## Task Description
Implement a complete binary search tree with the following requirements:

## Functional Requirements

### Binary Search Tree Operations
- Construct the binary tree through sequential integer insertions
- Implement the following methods:
  - `insert(item)`
  - `delete(item)`
  - Inorder traversal
  - Preorder traversal
  - Postorder traversal

### Traversal Output Specifications
- Traversal outputs should print values separated by spaces to `std::cout`

## Delete Operation Specification
- If the item is not in the tree, do not modify the tree
- When deleting a node, correctly reattach any disconnected subtrees
- For nodes with two children, use one of these strategies:
  1. Copy the in-order successor's value (smallest node in right subtree)
  2. Copy the in-order predecessor's value (largest node in left subtree)
  3. Then remove the original successor/predecessor node

## Level-Order Printing
Implement a function to print the tree "by levels":
- First line: root node
- Subsequent lines: node children
- Maintain tree structure in output
- Use 'X' to represent missing children
- Example output format:
  ```
  root
  left_child right_child
  left_grandchild right_grandchild left_grandchild right_grandchild
  ```

## Program Input and Output

### Input
- Program takes filename as command-line argument
- Input file contains space-separated integers

### Output Requirements
1. Postorder traversal
2. Preorder traversal
3. Inorder traversal
4. Level-order tree representation

## Example Inputs and Outputs

### Example 1: Input `1 2 3 4 5 6 7 8 9 10`
**Output:**
```
10 9 8 7 6 5 4 3 2 1 
1 2 3 4 5 6 7 8 9 10 
1 2 3 4 5 6 7 8 9 10 
1 
X 2 
X 3 
X 4 
X 5 
X 6 
X 7 
X 8 
X 9 
X 10 
X X 
```

### Example 2: Input `5 1 0 6 3 2 4 8 7`
**Output:**
```
0 2 4 3 1 7 8 6 5 
5 1 0 3 2 4 6 8 7 
0 1 2 3 4 5 6 7 8 
5 
1 6 
0 3 X 8 
X X 2 4 7 X 
X X X X X X 
```

### Example 3: Input `15 1 14 -3 20 40 33 32 5 4 3 12 77 45 63 50 51 25`
**Output:**
```
-3 3 4 12 5 14 1 25 32 33 51 50 63 45 77 40 20 15 
15 1 -3 14 5 4 3 12 20 40 33 32 25 77 45 63 50 51 
-3 1 3 4 5 12 14 15 20 25 32 33 40 45 50 51 63 77 
15 
1 20 
-3 14 X 40 
X X 5 X 33 77 
4 12 32 X 45 X 
3 X X X 25 X X 63 
X X X X 50 X 
X 51 
X X 
```

## Submission Requirements
- Submit a single `main.cpp` file
- Ensure code compiles with C++11 or later standard
- Handle potential input errors gracefully
