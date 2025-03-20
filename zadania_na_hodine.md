
# The tasks corresponding to the topics covered in the PRO lessons by Tom. Muc.

## Contains

## Method Overview:

**Prototype:** `bool rContains(Node* currentNode, int value);`

### Parameters:
- `currentNode`: A pointer to the current node in the tree being examined.
- `value`: The integer value being searched for within the tree.

### Return Value:
The method returns `true` if the value is found within the tree and `false` otherwise.

## Key Requirements:

### 1. Base Case - Node is nullptr:
If `currentNode` is `nullptr`, the function has reached a leaf node's child without finding the value, indicating the value is not present in the tree. Return `false` in this case.

### 2. Value Match:
If `currentNode->value` matches the searched value, the function has successfully found the value within the tree. Return `true`.

### 3. Recursive Search Logic:
- If the searched value is less than `currentNode->value`, recursively call `rContains` for the left child of the current node. This follows the BST property that all values in the left subtree are less than the node's value.
- Conversely, if the searched value is greater than `currentNode->value`, the function should recursively explore the right subtree by calling `rContains` for the right child. This is based on the BST property that all values in the right subtree are greater than the node's value.

## Implementation Strategy:
Utilize the structure and properties of a BST to efficiently navigate the search space. By comparing the searched value with each node's value, the function should halve the search space with each recursive call.

Ensure that your implementation correctly handles both base cases and recursive exploration of the tree.

## Constraints:
- Assume the Node structure is defined with `int value`, `Node* left`, and `Node* right`.
- The tree is assumed to be a BST, where for any given node, all values in its left subtree are less, and all values in its right subtree are greater than the node's value.

## Expected Behavior:

- For a BST containing the values `[20, 10, 30, 5, 15]`, a call to `rContains(root, 15)` should return `true`, indicating that the value 15 exists within the tree.
- A call to `rContains(root, 100)` should return `false`, indicating that the value 100 is not present in the tree.

---


```cpp


#include <iostream>

using namespace std;


class Node { 
    public: 
        int value;
        Node* left;
        Node* right;

        Node(int value) {
            this->value = value;
            left = nullptr;
            right = nullptr;
        }
};


class BinarySearchTree {
    public:
        Node* root;

    public:
        BinarySearchTree() { root = nullptr; }

        // ---------------------------------------------------
        //  Below is a helper function used by the destructor
        //  Deletes all nodes in BST
        //  Similar to DFS PostOrder in Tree Traversal section
        // ---------------------------------------------------
        void destroy(Node* currentNode) {
            if (currentNode == nullptr) return;
            if (currentNode->left) destroy(currentNode->left);
            if (currentNode->right) destroy(currentNode->right);
            delete currentNode;
        }

        ~BinarySearchTree() { destroy(root); }

        Node* getRoot() {
            return root;
        } 

        bool insert(int value) {
            Node* newNode = new Node(value);
            if (root == nullptr) {
                root = newNode;
                return true;
            }
            Node* temp = root;
            while(true) {
                if (newNode->value == temp->value) return false;
                if (newNode->value < temp->value) {
                    if (temp->left == nullptr) {
                        temp->left = newNode;
                        return true;
                    }
                    temp = temp->left;
                } else {
                    if (temp->right == nullptr) {
                        temp->right = newNode;
                        return true;
                    }
                    temp = temp->right;
                }
            }
        }


        //   +===================================================+
        //   |              WRITE YOUR CODE HERE                 |
        //   | Description:                                      |
        //   | - Recursively checks if a binary search tree      |
        //   |   contains a node with the given value.           |
        //   |                                                   |
        //   | Parameters:                                       |
        //   | - currentNode: The node currently being checked.  |
        //   | - value: The value being searched for.            |
        //   |                                                   |
        //   | Return:                                           |
        //   | - Returns true if the value is found in the tree; |
        //   |   otherwise, returns false.                       |
        //   |                                                   |
        //   | Behavior:                                         |
        //   | - Starts the search from the currentNode and      |
        //   |   traverses the tree down to its children based   |
        //   |   on the value being greater or lesser than the   |
        //   |   currentNode's value, following BST properties.  |
        //   | - If a null node is reached, the value is not     |
        //   |   present in the tree and false is returned.      |
        //   | - If the node with the value is found, returns    |
        //   |   true.                                           |
        //   +===================================================+

        bool rContains(int value) { 
            return rContains(root, value); 
        } 

};


```

---

# Insert

## Method Overview:

**Prototype:** `Node* rInsert(Node* currentNode, int value);`

### Parameters:
- `currentNode`: A pointer to the current node in the tree. Initially, this is the root of the BST.
- `value`: The integer value to be inserted into the BST.

### Return Value:
The method returns a pointer to the node, ensuring the tree remains connected after the insertion.

## Key Requirements:

### 1. Handling Null Nodes:
If `currentNode` is `nullptr`, this indicates the correct insertion point for the new value has been found. Create and return a new node with the specified value.

### 2. Recursive Insertion Logic:
- If the value is less than `currentNode->value`, recursively insert the new value into the left subtree.
- If the value is greater than `currentNode->value`, recursively insert the new value into the right subtree.

This recursive approach ensures the BST properties are maintained during insertion.

### 3. Returning the Current Node:
After possibly attaching a new node to the current node or simply traversing the tree, return `currentNode` to ensure the tree structure remains intact. This step is crucial for reconnecting the potentially modified subtree back to its parent.

## Implementation Strategy:
Leverage the BST's properties to determine the direction (left or right subtree) for each recursive insertion call.

Ensure the method appropriately creates new nodes when a suitable insertion point is found (`currentNode == nullptr`).

Maintain the tree's integrity by returning the `currentNode` at each step, ensuring that changes are reflected throughout the tree.

## Constraints:
- The tree is structured as a BST, where each node contains an integer value, and pointers to its left and right children (`Node* left`, `Node* right`).
- Assume the Node structure and necessary constructor are properly defined.

## Expected Behavior:
- Inserting a value into an empty tree should create a new root node with that value.
- Inserting a value into a non-empty tree should add the value in the correct location, maintaining the BST's ordered structure without duplicates.

---

```cpp


#include <iostream>

using namespace std;


class Node { 
    public: 
        int value;
        Node* left;
        Node* right;

        Node(int value) {
            this->value = value;
            left = nullptr;
            right = nullptr;
        }
};


class BinarySearchTree {
    private:
        Node* root;

    public:
        BinarySearchTree() { root = nullptr; }


        // ---------------------------------------------------
        //  Below is a helper function used by the destructor
        //  Deletes all nodes in BST
        //  Similar to DFS PostOrder in Tree Traversal section
        // ---------------------------------------------------
        void destroy(Node* currentNode) {
            if (currentNode == nullptr) return;
            if (currentNode->left) destroy(currentNode->left);
            if (currentNode->right) destroy(currentNode->right);
            delete currentNode;
        }

        ~BinarySearchTree() { destroy(root); }

        Node* getRoot() {
            return root;
        }   
        
        bool rContains(Node* currentNode, int value) {
            if (currentNode == nullptr) return false;
            
            if (currentNode->value == value) return true;
            
            if (value < currentNode->value) {
                return rContains(currentNode->left, value);
            } else {
                return rContains(currentNode->right, value);
            }
        }
        bool rContains(int value) { 
            return rContains(root, value); 
        } 

         bool insert(int value) {
            Node* newNode = new Node(value);
            if (root == nullptr) {
                root = newNode;
                return true;
            }
            Node* temp = root;
            while(true) {
                if (newNode->value == temp->value) return false;
                if (newNode->value < temp->value) {
                    if (temp->left == nullptr) {
                        temp->left = newNode;
                        return true;
                    }
                    temp = temp->left;
                } else {
                    if (temp->right == nullptr) {
                        temp->right = newNode;
                        return true;
                    }
                    temp = temp->right;
                }
            }
        }
               
//   +===================================================+
//   |              WRITE YOUR CODE HERE                 |
//   | Description:                                      |
//   | - Recursively inserts a new node with a given     |
//   |   value into a binary search tree.                |
//   |                                                   |
//   | Parameters:                                       |
//   | - currentNode: The node currently being examined. |
//   | - value: The value to insert into the tree.       |
//   |                                                   |
//   | Return:                                           |
//   | - Returns the node itself if it is not null.      |
//   | - If a null node is encountered, it creates and   |
//   |   returns a new node with the given value,        |
//   |   effectively inserting it into the tree.         |
//   |                                                   |
//   | Behavior:                                         |
//   | - The function traverses the tree starting from   |
//   |   the currentNode.                                |
//   | - Based on the value to be inserted, it explores  |
//   |   the left or right subtree.                      |
//   | - Insertion is done only if the correct position  |
//   |   (a null spot) in the tree is found, maintaining |
//   |   the BST property.                               |
//   | - The tree's structure is unaltered if the value  |
//   |   already exists in the tree.                     |
//   +===================================================+

        void rInsert(int value) { 
            if (root == nullptr) root = new Node(value);
            rInsert(root, value); 
        } 
        
};

```

---


# BST: Minimum Value

## Method Overview:

**Prototype:** `int minValue(Node* currentNode);`

### Parameter:
- `currentNode`: A pointer to the current node being inspected. Initially, this will be the root of the BST.

### Return Value:
The method returns the minimum integer value found in the BST.

## Key Requirements:

### 1. Iterative Traversal:
Begin at the node specified by `currentNode`. In the context of a BST, the minimum value is always located at the leftmost node.

Use a while loop to traverse the left children of the BST. Continue moving left until reaching a node that does not have a left child (`currentNode->left == nullptr`).

### 2. Finding the Minimum Value:
Once a node with no left child is reached, this node contains the minimum value in the BST. The property of the BST ensures that values decrease as you move left from the root.

## Implementation Notes:
The method must efficiently navigate through the BST, taking advantage of its properties to minimize the search space.

No recursive calls are necessary for this implementation; it relies on iterative traversal to find the minimum value.

## Constraints:
- The provided BST structure follows the standard definition, where each node contains a value, and pointers to left and right children (`left` and `right`).
- Assume the Node structure and the BST are well-formed and valid.

## Example Usage:
If the BST contains nodes with the values `[20, 10, 30, 5, 15]`, calling `minValue(root)` (where `root` points to the root of the BST) should return `5`, as it is the smallest value in the tree.

---

```cpp
#include <iostream>

using namespace std;


class Node { 
    public: 
        int value;
        Node* left;
        Node* right;

        Node(int value) {
            this->value = value;
            left = nullptr;
            right = nullptr;
        }
};


class BinarySearchTree {
    public:
        Node* root;

    public:
        BinarySearchTree() { root = nullptr; }


        // ---------------------------------------------------
        //  Below is a helper function used by the destructor
        //  Deletes all nodes in BST
        //  Similar to DFS PostOrder in Tree Traversal section
        // ---------------------------------------------------
        void destroy(Node* currentNode) {
            if (currentNode == nullptr) return;
            if (currentNode->left) destroy(currentNode->left);
            if (currentNode->right) destroy(currentNode->right);
            delete currentNode;
        }

        ~BinarySearchTree() { destroy(root); }

        Node* getRoot() {
            return root;
        } 
                
        Node* rInsert(Node* currentNode, int value) {
            if (currentNode == nullptr) return new Node(value);
        
            if (value < currentNode->value) {
                currentNode->left = rInsert(currentNode->left, value);
            } else if (value > currentNode->value) {
                currentNode->right = rInsert(currentNode->right, value);
            } 
            return currentNode;
        }
        void rInsert(int value) { 
            if (root == nullptr) root = new Node(value);
            rInsert(root, value); 
        } 

        //   +===================================================+
        //   |              WRITE YOUR CODE HERE                 |
        //   | Description:                                      |
        //   | - Finds the minimum value in a binary search tree |
        //   |   by traversing down the left children of nodes.  |
        //   |                                                   |
        //   | Parameters:                                       |
        //   | - currentNode: The starting node of the tree.     |
        //   |                                                   |
        //   | Return:                                           |
        //   | - Returns the value of the leftmost node, which   |
        //   |   represents the minimum value in the tree.       |
        //   |                                                   |
        //   | Behavior:                                         |
        //   | - The method iteratively moves to the left child  |
        //   |   of each node, reaching the leftmost node which  |
        //   |   does not have a left child.                     |
        //   | - This leftmost node contains the minimum value   |
        //   |   in the tree, following the properties of a BST. |
        //   +===================================================+

};
```

---


# Delete

## Method Overview:

**Prototype:** `Node* deleteNode(Node* currentNode, int value);`

### Parameters:
- `currentNode`: A pointer to the current node being inspected. Initially, this will be the root of the BST.
- `value`: The integer value of the node to be removed from the tree.

### Return Value:
The method returns a pointer to the node, potentially adjusted to ensure the BST structure remains valid post-deletion.

## Key Requirements:

### 1. Node Not Found:
If `currentNode` is `nullptr`, it indicates the value does not exist in the BST. Return `nullptr`.

### 2. Recursive Deletion:
- If the value is less than `currentNode->value`, recursively search for the value to delete in the left subtree.
- If the value is greater than `currentNode->value`, recursively search in the right subtree.

### 3. Node Deletion Scenarios:

#### Leaf Node:
If the node to delete is a leaf (no children), simply delete it and return `nullptr`.

#### One Child:
If the node has only one child, delete the node and return its child, effectively replacing the node with its child.

#### Two Children:
If the node has two children:
- Find the minimum value in the right subtree (to maintain the BST properties).
- Replace the value of the node to be deleted with this minimum value.
- Recursively delete the node that originally had this minimum value in the right subtree.

### 4. Maintaining the BST Structure:
Ensure the tree remains a valid BST after the deletion. This includes maintaining the property that all values in the left subtree are less than the node's value, and all values in the right subtree are greater.

## Functionality to Utilize:
- Utilize the provided `minValue` function to find the minimum value in the right subtree when deleting a node with two children.
- Ensure correct memory management by properly deleting nodes that are removed from the tree to prevent memory leaks.

## Constraints:
- Assume the Node structure contains `int value`, `Node* left`, and `Node* right`.
- The BST is well-formed, meaning it adheres to the properties of a binary search tree.

## Example Usage:
If the BST contains nodes with values `[10, 5, 15, 2, 7, 12, 18]` and `deleteNode(root, 15)` is called:

The method should remove the node with value 15 and adjust the BST to remain valid, potentially by replacing the deleted node's value with a successor or predecessor value, depending on the node's children.

---

```cpp
#include <iostream>

using namespace std;


class Node { 
    public: 
        int value;
        Node* left;
        Node* right;

        Node(int value) {
            this->value = value;
            left = nullptr;
            right = nullptr;
        }
};


class BinarySearchTree {
    public:
        Node* root;

    public:
        BinarySearchTree() { root = nullptr; }


        // ---------------------------------------------------
        //  Below is a helper function used by the destructor
        //  Deletes all nodes in BST
        //  Similar to DFS PostOrder in Tree Traversal section
        // ---------------------------------------------------
        void destroy(Node* currentNode) {
            if (currentNode == nullptr) return;
            if (currentNode->left) destroy(currentNode->left);
            if (currentNode->right) destroy(currentNode->right);
            delete currentNode;
        }

        ~BinarySearchTree() { destroy(root); }

        Node* getRoot() {
            return root;
        } 
        
        Node* rInsert(Node* currentNode, int value) {
            if (currentNode == nullptr) return new Node(value);
        
            if (value < currentNode->value) {
                currentNode->left = rInsert(currentNode->left, value);
            } else if (value > currentNode->value) {
                currentNode->right = rInsert(currentNode->right, value);
            } 
            return currentNode;
        }
        void rInsert(int value) { 
            if (root == nullptr) root = new Node(value);
            rInsert(root, value); 
        } 
        
        bool rContains(Node* currentNode, int value) {
            if (currentNode == nullptr) return false;
            
            if (currentNode->value == value) return true;
            
            if (value < currentNode->value) {
                return rContains(currentNode->left, value);
            } else {
                return rContains(currentNode->right, value);
            }
        }
        bool rContains(int value) { 
            return rContains(root, value); 
        } 

        int minValue(Node* currentNode) {
            while (currentNode->left != nullptr) {
                currentNode = currentNode->left;
            }
            return currentNode->value;
        } 
              
        //   +===================================================+
        //   |              WRITE YOUR CODE HERE                 |
        //   | Description:                                      |
        //   | - Deletes a node with a specific value from a     |
        //   |   binary search tree (BST) and maintains the      |
        //   |   BST properties after deletion.                  |
        //   |                                                   |
        //   | Parameters:                                       |
        //   | - currentNode: The node currently being examined. |
        //   | - value: The value of the node to be deleted.     |
        //   |                                                   |
        //   | Return:                                           |
        //   | - The modified tree's root node after deletion.   |
        //   |                                                   |
        //   | Behavior:                                         |
        //   | - If the value is less/more than the current node,|
        //   |   recursively search in the left/right subtree.   |
        //   | - If the node to delete is found and has no child,|
        //   |   delete the node and return null.                |
        //   | - If the node has one child, delete the node and  |
        //   |   return the child.                               |
        //   | - If the node has two children, find the minimum  |
        //   |   value in the right subtree, replace the node's  |
        //   |   value with this minimum value, and then delete  |
        //   |   the minimum value node in the right subtree.    |
        //   +===================================================+

        void deleteNode(int value) { root = deleteNode(root, value); }

};



```

---


# BST: Breadth First Search (BFS)

## Method Overview:

**Function Signature:** `void BFS();`

### Tasks:
The function performs a **Breadth-First Search (BFS)** traversal on the binary search tree. During the traversal, it prints the node values in the order they are visited.

### Steps for BFS Implementation:

1. **Create a queue:**
   - Declare a queue `myQueue` of type `queue<Node*>` to store the nodes in the order they will be visited.

2. **Enqueue the root node:**
   - If the root pointer is not `nullptr`, push it onto `myQueue`.

3. **Traverse the binary search tree:**
   - While the queue is not empty, perform the following actions:
     1. **Dequeue the front node** in `myQueue` and store it in a `Node*` variable called `currentNode`.
     2. **Print the value** of `currentNode`.
     3. If the **left child** of `currentNode` exists, enqueue it.
     4. If the **right child** of `currentNode` exists, enqueue it.

### Example of BFS Traversal:

For a Binary Search Tree with the following values:

```
        10
       /        5   15
     / \   /     2   7 12 18
```

Performing a BFS traversal will result in the following order of node values:

```
10, 5, 15, 2, 7, 12, 18
```

The function starts at the root (10), then proceeds to its children (5 and 15), and continues level by level.

### Constraints:
- The function assumes that the tree is well-formed.
- The tree follows the properties of a binary search tree (BST).

## Expected Behavior:
Calling `BFS()` on the tree will print the node values in the order they are visited during the BFS traversal.

```cpp 
#include <iostream>
#include <queue>

using namespace std;


class Node { 
    public: 
        int value;
        Node* left;
        Node* right;

        Node(int value) {
            this->value = value;
            left = nullptr;
            right = nullptr;
        }
};


class BinarySearchTree {
    private:
        Node* root;

    public:
        BinarySearchTree() { root = nullptr; }


        // ---------------------------------------------------
        //  This is a helper function used by the destructor
        //  Deletes all nodes in BST
        //  Similar to DFS PostOrder in Tree Traversal section
        // ---------------------------------------------------
        void destroy(Node* currentNode) {
            if (currentNode == nullptr) return;
            if (currentNode->left) destroy(currentNode->left);
            if (currentNode->right) destroy(currentNode->right);
            delete currentNode;
        }

        ~BinarySearchTree() { destroy(root); }

        Node* getRoot() {
            return root;
        } 

        bool insert(int value) {
            Node* newNode = new Node(value);
            if (root == nullptr) {
                root = newNode;
                return true;
            }
            Node* temp = root;
            while(true) {
                if (newNode->value == temp->value) return false;
                if (newNode->value < temp->value) {
                    if (temp->left == nullptr) {
                        temp->left = newNode;
                        return true;
                    }
                    temp = temp->left;
                } else {
                    if (temp->right == nullptr) {
                        temp->right = newNode;
                        return true;
                    }
                    temp = temp->right;
                }
            }
        }

		//   +=====================================================+
		//   |                WRITE YOUR CODE HERE                 |
		//   | Description:                                        |
		//   | - This method performs a Breadth-First Search       |
		//   |   (BFS) starting from the root of the tree.         |
		//   | - Prints the value of each node as it visits it.    |
		//   |                                                     |
		//   | Return type: void                                   |
		//   |                                                     |
		//   | Tips:                                               |
		//   | - Uses a queue (myQueue) to keep track of nodes     |
		//   |   to visit.                                         |
		//   | - Check output from Test.cpp in "User logs".        |
		//   +=====================================================+

};
```

---

# BST: DFS PreOrder

## Method Overview:

**Function Signature:** `void DFSPreOrder(Node* currentNode);`

### Tasks:
The function performs a **Depth-First Search (DFS)** traversal using the **Pre-Order** method. During the traversal, it prints the node values in the order they are visited.

### Steps for PreOrder DFS Implementation:

1. **Print the value of the current node:**
   - Print the value of `currentNode`.

2. **Traverse the left subtree:**
   - If the left child of `currentNode` exists (i.e., `currentNode->left` is not `nullptr`), recursively call `DFSPreOrder` with the left child as the argument.

3. **Traverse the right subtree:**
   - If the right child of `currentNode` exists (i.e., `currentNode->right` is not `nullptr`), recursively call `DFSPreOrder` with the right child as the argument.

### Example of PreOrder DFS Traversal:

For a Binary Search Tree with the following values:

```
        10
       /        5   15
     / \   /     2   7 12 18
```

Performing a DFS PreOrder traversal will result in the following order of node values:

```
10, 5, 2, 7, 15, 12, 18
```

The traversal starts at the root (10), then moves to its left subtree (5, 2, 7), and finally traverses the right subtree (15, 12, 18).

### Constraints:
- The function assumes that the tree is well-formed.
- The tree follows the properties of a binary search tree (BST).

## Expected Behavior:
Calling `DFSPreOrder()` on the tree will print the node values in the order they are visited during the Pre-Order Depth-First Search traversal.
---

```cpp

#include <iostream>

using namespace std;


class Node { 
    public: 
        int value;
        Node* left;
        Node* right;

        Node(int value) {
            this->value = value;
            left = nullptr;
            right = nullptr;
        }
};


class BinarySearchTree {
    private:
        Node* root;

    public:
        BinarySearchTree() { root = nullptr; }


        // ---------------------------------------------------
        //  This is a helper function used by the destructor
        //  Deletes all nodes in BST
        //  Similar to DFS PostOrder in Tree Traversal section
        // ---------------------------------------------------
        void destroy(Node* currentNode) {
            if (currentNode == nullptr) return;
            if (currentNode->left) destroy(currentNode->left);
            if (currentNode->right) destroy(currentNode->right);
            delete currentNode;
        }

        ~BinarySearchTree() { destroy(root); }

        Node* getRoot() {
            return root;
        } 

        bool insert(int value) {
            Node* newNode = new Node(value);
            if (root == nullptr) {
                root = newNode;
                return true;
            }
            Node* temp = root;
            while(true) {
                if (newNode->value == temp->value) return false;
                if (newNode->value < temp->value) {
                    if (temp->left == nullptr) {
                        temp->left = newNode;
                        return true;
                    }
                    temp = temp->left;
                } else {
                    if (temp->right == nullptr) {
                        temp->right = newNode;
                        return true;
                    }
                    temp = temp->right;
                }
            }
        }


		//   +=====================================================+
		//   |                WRITE YOUR CODE HERE                 |
		//   | Description:                                        |
		//   | - This method performs a Depth-First Search         |
		//   |   (DFS) using Pre-Order traversal.                  |
		//   | - Starts at the given 'currentNode' and goes        |
		//   |   down its children.                                |
		//   | - Prints the value of each node as it visits it.    |
		//   |                                                     |
		//   | Return type: void                                   |
		//   |                                                     |
		//   | Tips:                                               |
		//   | - Uses recursion for traversal.                     |
		//   | - Base case returns if currentNode is null.         |
		//   | - Check output from Test.cpp in "User logs".        |
		//   +=====================================================+
 
        
        void DFSPreOrder() {
            DFSPreOrder(root);
        }

};

```
---

# BST: DFS PostOrder

## Method Overview:

**Function Signature:** `void DFSPostOrder(Node* currentNode);`

### Tasks:
The function performs a **Depth-First Search (DFS)** traversal using the **Post-Order** method. During the traversal, it prints the node values in the order they are visited.

### Steps for PostOrder DFS Implementation:

1. **Traverse the left subtree:**
   - If the left child of `currentNode` exists (i.e., `currentNode->left` is not `nullptr`), recursively call `DFSPostOrder` with the left child as the argument.

2. **Traverse the right subtree:**
   - If the right child of `currentNode` exists (i.e., `currentNode->right` is not `nullptr`), recursively call `DFSPostOrder` with the right child as the argument.

3. **Print the value of the current node:**
   - After traversing the left and right subtrees, print the value of `currentNode`.

### Example of PostOrder DFS Traversal:

For a Binary Search Tree with the following values:

```
        10
       /        5   15
     / \   /     2   7 12 18
```

Performing a DFS PostOrder traversal will result in the following order of node values:

```
2, 7, 5, 12, 18, 15, 10
```

The traversal starts at the root (10), then moves to its left subtree (2, 7, 5), and finally traverses the right subtree (12, 18, 15), printing the root value at the end.

### Constraints:
- The function assumes that the tree is well-formed.
- The tree follows the properties of a binary search tree (BST).

## Expected Behavior:
Calling `DFSPostOrder()` on the tree will print the node values in the order they are visited during the Post-Order Depth-First Search traversal.

--- 

```cpp

#include <iostream>

using namespace std;


class Node { 
    public: 
        int value;
        Node* left;
        Node* right;

        Node(int value) {
            this->value = value;
            left = nullptr;
            right = nullptr;
        }
};


class BinarySearchTree {
    private:
        Node* root;

    public:
        BinarySearchTree() { root = nullptr; }


        // ---------------------------------------------------
        //  This is a helper function used by the destructor
        //  Deletes all nodes in BST
        //  Similar to DFS PostOrder in Tree Traversal section
        // ---------------------------------------------------
        void destroy(Node* currentNode) {
            if (currentNode == nullptr) return;
            if (currentNode->left) destroy(currentNode->left);
            if (currentNode->right) destroy(currentNode->right);
            delete currentNode;
        }

        ~BinarySearchTree() { destroy(root); }

        Node* getRoot() {
            return root;
        } 

        bool insert(int value) {
            Node* newNode = new Node(value);
            if (root == nullptr) {
                root = newNode;
                return true;
            }
            Node* temp = root;
            while(true) {
                if (newNode->value == temp->value) return false;
                if (newNode->value < temp->value) {
                    if (temp->left == nullptr) {
                        temp->left = newNode;
                        return true;
                    }
                    temp = temp->left;
                } else {
                    if (temp->right == nullptr) {
                        temp->right = newNode;
                        return true;
                    }
                    temp = temp->right;
                }
            }
        }


		//   +=====================================================+
		//   |                    WRITE YOUR CODE HERE             |
		//   | Description:                                        |
		//   | - This method performs a Depth-First Search         |
		//   |   (DFS) using Post-Order traversal.                 |
		//   | - Starts at the given 'currentNode' and goes        |
		//   |   down its children before printing its value.      |
		//   |                                                     |
		//   | Return type: void                                   |
		//   |                                                     |
		//   | Tips:                                               |
		//   | - Uses recursion for traversal.                     |
		//   | - Base case returns if currentNode is null.         |
		//   | - Check output from Test.cpp in "User logs".        |
		//   +=====================================================+

        
        void DFSPostOrder() {
            DFSPostOrder(root);
        }

};

```

---

# BST: DFS InOrder

## Method Overview:

**Function Signature:** `void DFSInOrder(Node* currentNode);`

### Tasks:
The function performs a **Depth-First Search (DFS)** traversal using the **In-Order** method. During the traversal, it prints the node values in the order they are visited.

### Steps for InOrder DFS Implementation:

1. **Traverse the left subtree:**
   - If the left child of `currentNode` exists (i.e., `currentNode->left` is not `nullptr`), recursively call `DFSInOrder` with the left child as the argument.

2. **Print the value of the current node:**
   - After traversing the left subtree, print the value of `currentNode`.

3. **Traverse the right subtree:**
   - If the right child of `currentNode` exists (i.e., `currentNode->right` is not `nullptr`), recursively call `DFSInOrder` with the right child as the argument.

### Example of InOrder DFS Traversal:

For a Binary Search Tree with the following values:

```
        10
       /        5   15
     / \   /     2   7 12 18
```

Performing a DFS InOrder traversal will result in the following order of node values:

```
2, 5, 7, 10, 12, 15, 18
```

The traversal starts at the leftmost node (2), then moves up to 5, 7, the root (10), and continues to the right subtree (12, 15, 18).

### Constraints:
- The function assumes that the tree is well-formed.
- The tree follows the properties of a binary search tree (BST).

## Expected Behavior:
Calling `DFSInOrder()` on the tree will print the node values in the order they are visited during the In-Order Depth-First Search traversal.
---
```cpp 

#include "BinarySearchTree.h"


Node::Node(int value) {
    this->value = value;
    left = nullptr;
    right = nullptr;
}

BinarySearchTree::BinarySearchTree() {
    root = nullptr;
}

BinarySearchTree::~BinarySearchTree() {
    destroy(root);
}

// ---------------------------------------------------
// Helper function used by destructor
// Deletes all nodes in BST
// Similar to DFS PostOrder in Tree Traversal section
// ---------------------------------------------------
void BinarySearchTree::destroy(Node* currentNode) {
    if (currentNode) {
        destroy(currentNode->left);
        destroy(currentNode->right);
        delete currentNode;
    }
}

void BinarySearchTree::insert(int value) {
    Node* newNode = new Node(value);
    if (root == nullptr) {
        root = newNode;
        return;
    }
    Node* temp = root;
    while(true) {
        if (newNode->value == temp->value) return;
        if (newNode->value < temp->value) {
            if (temp->left == nullptr) {
                temp->left = newNode;
                return;
            }
            temp = temp->left;
        } else {
            if (temp->right == nullptr) {
                temp->right = newNode;
                return;
            }
            temp = temp->right;
        }
    }
}

bool BinarySearchTree::contains(int value) {
    if (root == nullptr) return false;
    Node* temp = root;
    while(temp) {
        if (value < temp->value) {
            temp = temp->left;
        } else if (value > temp->value) {
            temp = temp->right;
        } else {
            return true;
        }
    }
    return false;
}

void BinarySearchTree::BFS() {
    Node* currentNode = root;
    queue<Node*> myQueue;
    myQueue.push(currentNode);

    while (myQueue.size() > 0) {
        currentNode = myQueue.front();
        myQueue.pop();
        cout << currentNode->value << " ";
        if (currentNode->left) {
            myQueue.push(currentNode->left);
        }
        if (currentNode->right) {
            myQueue.push(currentNode->right);
        }
    }
}

void BinarySearchTree::DFSPreOrder(Node* currentNode) {
    cout << currentNode->value << " ";
    if (currentNode->left != nullptr) {
        DFSPreOrder(currentNode->left);
    }
    if (currentNode->right != nullptr) {
        DFSPreOrder(currentNode->right);
    }
}

void BinarySearchTree::DFSPreOrder() {
    DFSPreOrder(root);
}

void BinarySearchTree::DFSPostOrder(Node* currentNode) {
    if (currentNode->left != nullptr) {
        DFSPostOrder(currentNode->left);
    }
    if (currentNode->right != nullptr) {
        DFSPostOrder(currentNode->right);
    }
    cout << currentNode->value << " ";
}

void BinarySearchTree::DFSPostOrder() {
    DFSPostOrder(root);
}

void BinarySearchTree::DFSInOrder(Node* currentNode) {
    // FINISH WRITING THE DFS_IN_ORDER MEMBER FUNCTION HERE //
    //                                                      //
    //                                                      //
    //                                                      //
    //                                                      //
    //////////////////////////////////////////////////////////
}

void BinarySearchTree::DFSInOrder() {
    DFSInOrder(root);
}

```

---


# Bubble Sort

## Method Overview:

**Function Signature:** `void bubbleSort(int array[], int size);`

### Parameters:
- `array[]`: An array of integers to be sorted.
- `size`: The size of the array.

### Key Requirements:

1. **Iterate through the array:**
   - Use a loop with an index variable `i` decreasing from `size - 1` to 1.
   
2. **Compare adjacent elements:**
   - Within the loop, create another loop with an index variable `j` increasing from 0 to `i - 1`. Compare the elements at positions `j` and `j + 1`.

3. **Swap elements if necessary:**
   - If the element at position `j` is greater than the element at position `j + 1`, swap the elements:
     1. Store the element at position `j` in a temporary variable `temp`.
     2. Assign the element at position `j + 1` to the element at position `j`.
     3. Assign the value stored in `temp` to the element at position `j + 1`.

### Example of Bubble Sort:

Given the array:

```
[64, 34, 25, 12, 22, 11, 90]
```

Performing a bubble sort will result in the following sorted array:

```
[11, 12, 22, 25, 34, 64, 90]
```

### Constraints:
- The sorting is done in-place, meaning the input array is modified directly.

## Expected Behavior:
After calling `bubbleSort()`, the input array will be sorted in ascending order.




---
```cpp
#include "BubbleSort.h"


void bubbleSort(int array[], int size) {
	//   +=====================================================+
	//   |                 WRITE YOUR CODE HERE                |
	//   | Description:                                        |
	//   | - This function sorts an array using the            |
	//   |   Bubble Sort algorithm.                            |
	//   | - It compares adjacent elements and swaps them if   |
	//   |   they're in the wrong order.                       |
	//   |                                                     |
	//   | Return type: void                                   |
	//   |                                                     |
	//   | Tips:                                               |
	//   | - 'temp' is used for swapping elements.             |
	//   | - The outer loop decreases in size each iteration.  |
	//   | - Inner loop iterates up to 'i'.                    |
	//   | - Check output from Test.cpp in "User logs".        |
	//   +=====================================================+
}
```
---


# Selection Sort

## Method Overview:

**Function Signature:** `void selectionSort(int array[], int size);`

### Parameters:
- `array[]`: An array of integers to be sorted.
- `size`: The size of the array.

### Key Requirements:

1. **Iterate through the array:**
   - Use a loop with an index variable `i` increasing from 0 to `size - 1`.

2. **Find the index of the minimum element:**
   - Initialize a variable `minIndex` to `i`, and create another loop with an index variable `j` increasing from `i + 1` to `size - 1`. If the element at position `j` is less than the element at position `minIndex`, update `minIndex` to `j`.

3. **Swap the found minimum element with the element at position i:**
   - If `i` is not equal to `minIndex`, swap the elements:
     1. Store the element at position `i` in a temporary variable `temp`.
     2. Assign the element at position `minIndex` to the element at position `i`.
     3. Assign the value stored in `temp` to the element at position `minIndex`.

### Example of Selection Sort:

Given the array:

```
[64, 34, 25, 12, 22, 11, 90]
```

Performing a selection sort will result in the following sorted array:

```
[11, 12, 22, 25, 34, 64, 90]
```

### Constraints:
- The sorting is done in-place, meaning the input array is modified directly.

## Expected Behavior:
After calling `selectionSort()`, the input array will be sorted in ascending order.

---

```cpp
#include "SelectionSort.h"


void selectionSort(int array[], int size) {
	//   +=====================================================+
	//   |                 WRITE YOUR CODE HERE                |
	//   | Description:                                        |
	//   | - This function sorts an array using the            |
	//   |   Selection Sort algorithm.                         |
	//   | - It finds the minimum element and swaps it with    |
	//   |   the first element, then repeats for the remaining.|
	//   |                                                     |
	//   | Return type: void                                   |
	//   |                                                     |
	//   | Tips:                                               |
	//   | - 'minIndex' holds the index of the smallest        |
	//   |   element found.                                    |
	//   | - 'temp' is used for swapping elements.             |
	//   | - Swap only if 'i' and 'minIndex' are different.    |
	//   | - Check output from Test.cpp in "User logs".        |
	//   +=====================================================+
}
```
---

# Insertion Sort

## Method Overview:

**Function Signature:** `void insertionSort(int array[], int size);`

### Parameters:
- `array[]`: An array of integers to be sorted.
- `size`: The size of the array.

### Key Requirements:

1. **Iterate through the array:**
   - Use a loop with an index variable `i` increasing from 1 to `size - 1`.

2. **Store the current element in a temporary variable:**
   - Store the element at position `i` in a temporary variable `temp`.

3. **Find the correct position for the current element:**
   - Initialize an index variable `j` to `i - 1`. Using a `while` loop, check if `j` is greater than or equal to 0 and if the element in the temporary variable `temp` is less than the element at position `j`. 
   - If both conditions are true, shift the element at position `j` one position to the right (to position `j + 1)`, and update the element at position `j` with the value stored in `temp`. Finally, decrement `j`.

### Example of Insertion Sort:

Given the array:

```
[64, 34, 25, 12, 22, 11, 90]
```

Performing an insertion sort will result in the following sorted array:

```
[11, 12, 22, 25, 34, 64, 90]
```

### Constraints:
- The sorting is done in-place, meaning the input array is modified directly.

## Expected Behavior:
After calling `insertionSort()`, the input array will be sorted in ascending order.

---
```cpp

#include "InsertionSort.h"


void insertionSort(int array[], int size) {
	//   +=====================================================+
	//   |                 WRITE YOUR CODE HERE                |
	//   | Description:                                        |
	//   | - This function sorts an array using the            |
	//   |   Insertion Sort algorithm.                         |
	//   | - It iterates through 'array[]' to place each       |
	//   |   element in its correct position.                  |
	//   |                                                     |
	//   | Return type: void                                   |
	//   |                                                     |
	//   | Tips:                                               |
	//   | - 'temp' holds the current element being examined.  |
	//   | - 'j' is used to find the correct position for      |
	//   |   'temp'.                                           |
	//   | - 'array[j+1]' and 'array[j]' are swapped as needed.|
	//   | - Check output from Test.cpp in "User logs".        |
	//   +=====================================================+
}
```
---
