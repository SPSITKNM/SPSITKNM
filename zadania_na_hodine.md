
# Contains

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



