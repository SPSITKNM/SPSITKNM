# Algorithmic Problem-Solving Challenges by Tomáš Mucha

## Introduction
Welcome to a series of challenging algorithmic assignments by Tomáš Mucha designed to deepen your understanding of fundamental data structures and problem-solving techniques in C++. These projects will test your ability to implement complex algorithms, manage data structures, and develop efficient solutions to classic computational problems.

## Challenge Overview

### 1. Binary Search Tree Implementation
**Focus:** Data Structure Design and Tree Traversals
- Learn to create a robust binary search tree
- Master tree manipulation techniques
- Implement multiple traversal methods
- Handle complex tree operations like insertion and deletion

### 2. Kruskal's Minimum Spanning Tree Algorithm
**Focus:** Graph Algorithms and Optimization
- Understand graph theory fundamentals
- Implement an efficient minimum spanning tree algorithm
- Learn about Union-Find data structure
- Practice handling complex graph representations

### 3. Subset Sum Problem
**Focus:** Recursive Backtracking and Combinatorial Search
- Explore recursive problem-solving techniques
- Develop efficient search and pruning strategies
- Handle combinatorial complexity
- Learn to optimize algorithmic approaches

## Tips for Success
- Read problem descriptions carefully
- Break down problems into smaller, manageable components
- Test your implementation with multiple input scenarios
- Focus on code readability and efficiency
- Use version control (e.g., git) to track your progress

## Recommended Preparation
- Review your understanding of:
  - Recursive algorithms
  - Data structures (trees, graphs)
  - Basic algorithm complexity analysis
- Practice implementing solutions incrementally
- Don't hesitate to ask for guidance or clarification

## Challenge Mindset
These problems are designed to be challenging. Embrace the learning process, experiment with different approaches, and don't get discouraged by initial difficulties.

**Good luck, and happy coding Tom. Muc.!**

---

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

--- 

# Kruskal's Minimum Spanning Tree Algorithm Assignment

## Problem Description
Implement Kruskal's algorithm to find the Minimum Spanning Tree (MST) of a weighted, connected graph.

## Algorithm Requirements

### Input
- A weighted graph represented as an adjacency matrix
- `0` indicates no edge between vertices
- Non-zero values represent edge weights

### Output
- Total weight of the Minimum Spanning Tree

### Algorithm Steps
1. Sort all edges in non-decreasing order of their weights
2. Use Union-Find data structure to detect cycles
3. Select edges that do not form a cycle
4. Stop when MST contains `|V| - 1` edges

## Implementation Details

### Union-Find Data Structure
- Implement with path compression
- Use union by rank optimization
- Efficiently handle set operations and cycle detection

### Key Functions
- `find(x)`: Find the representative/root of a set
- `unionSets(x, y)`: Merge two sets, return false if would create a cycle

## Test Cases

### Test Case 1
**Input:**
```
0 2 0 6 0
2 0 3 8 5
0 3 0 0 7
6 8 0 0 9
0 5 7 9 0
```
**Expected Output:** `16`

### Test Case 2
**Input:**
```
0 0 5 0 0 20 14 7 10 0
0 0 0 9 0 0 0 8 10 10
5 0 0 6 1 2 0 5 0 0
0 9 6 0 0 0 10 12 0 0
0 0 1 0 0 0 9 0 0 0
20 0 2 0 0 0 0 7 0 7
14 0 0 10 9 0 0 18 5 0
7 8 5 12 0 7 18 0 16 7
10 10 0 0 0 0 5 16 0 1
0 10 0 0 0 7 0 7 1 0
```
**Expected Output:** `40`

### Test Case 3
**Input:** (large graph with 20 vertices)
**Expected Output:** `119`

## Submission Requirements
- Submit a single `main.cpp` file
- Implement using C++11 or later
- Handle input file parsing
- Correctly implement Kruskal's algorithm
- Efficiently detect and prevent cycles

## Hints
- Use Union-Find data structure for cycle detection
- Sort edges by weight before processing
- Terminate when MST is complete (`|V| - 1` edges)

---

# Subset Sum Problem Assignment

## Problem Description
Write a program that finds all subsets of a given set of positive integers that sum up to a target value.

## Algorithmic Approach
Implement a backtracking algorithm to solve the subset sum problem:
- Explore all possible subset combinations
- Use recursive approach to generate subsets
- Prune unnecessary branches by tracking current sum

## Problem Requirements

### Input Specification
1. Input file format:
   - Contains a sequence of positive integers
   - Numbers are space-separated on a single line
2. Command-line arguments:
   - Filename containing input numbers
   - Target sum value

### Output Specification
- Print the total number of subsets that sum exactly to the target value
- Output should be a single integer

## Algorithm Design Guidelines
- Use recursive backtracking technique
- For each element, decide whether to:
  - Include it in the current subset
  - Exclude it from the current subset
- Optimize by stopping search branches that exceed target sum

## Example Test Cases

### Test Case 1
- Input file: `2 3 5 7`
- Target sum: `10`
- Expected output: `2`
- Explanation: Possible subsets are [2,3,5] and [3,7]

### Test Case 2
- Input file: `2 3 5 7`
- Target sum: `50`
- Expected output: `0`
- Explanation: No subset sums exactly to 50

## Implementation Constraints
- Use C++ 
- Implement recursive backtracking
- Handle input file parsing
- Efficiently track and count valid subsets

## Additional Challenges
- Consider time and space complexity
- Optimize pruning of search branches
- Handle large input sets efficiently

## Recommended Resources
- Levitin's Algorithm Design book
- Algorithms textbooks covering backtracking techniques
- Online algorithm design resources

## Submission Requirements
- Submit a single `main.cpp` file
- Ensure clean, readable code
- Include appropriate comments
- Handle potential input errors

## Hints
- Use vector to store input numbers
- Recursive function should take current index, current sum, and current subset
- Backtrack by including/excluding each number
- Prune branches that exceed target sum
