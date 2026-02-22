C Program: Height of a Binary Tree (Using Recursion)

This project demonstrates how to calculate the *height of a Binary Tree* in C using a recursive approach.

---

Description

This program:

* Defines a binary tree node using a struct
* Dynamically creates nodes using malloc()
* Calculates the *height of a binary tree*
* Demonstrates the height calculation on:

  * A balanced tree
  * A right-skewed tree

The height is calculated using recursion by finding the maximum height of left and right subtrees.

---

What is the Height of a Binary Tree?

The *height of a binary tree* is defined as:

> The number of edges on the longest path from the root node to a leaf node.

In this program:

* An empty tree has a height of *-1*
* A tree with only one node has a height of *0*

---

Example Tree 1

![Image](https://www.crio.do/blog/content/images/2022/02/Diagram-of-Binary-Tree.png)

![Image](https://deen3evddmddt.cloudfront.net/uploads/content-images/balanced-binary-tree-height.webp)

Structure:


        1
       / \
      2   3
     / \
    4   5


* Longest path: 1 → 2 → 4
* Height = *2*

---

## 🌿 Example Tree 2 (Right Skewed Tree)

![Image](https://www.researchgate.net/publication/258651397/figure/fig2/AS%3A297359331348481%401447907397353/Right-Skewed-Binary-Tree-Containing-5-nodes.png)

![Image](https://scaler.com/topics/images/degenerate-binary-trees.webp)

Structure:


1
 \
  2
   \
    3
     \
      4


* Longest path: 1 → 2 → 3 → 4
* Height = *3*

---

Source Code

c

#include <stdio.h>

#include <stdlib.h>

// A structure to represent a binary tree node

struct Node {
    
    int data;
    struct Node *left;
    struct Node *right;
};

// Function to create a new node

struct Node* newNode(int data) {
    
    struct Node* node = (struct Node*)malloc(sizeof(struct Node));
    
    node->data = data;
    node->left = NULL;
    node->right = NULL;
    return node;
}

// Function to calculate the height of a tree using recursion

int height(struct Node* node) {
    
    // Base case: an empty tree has a height of -1 
    
    if (node == NULL) {
        return -1;
    } else {
        int leftHeight = height(node->left);
        int rightHeight = height(node->right);

        if (leftHeight > rightHeight) {
            return(leftHeight + 1);
        } else {
            return(rightHeight + 1);
        }
    }
}

// Main function

int main() {
    
    struct Node* root = newNode(1);
    root->left = newNode(2);
    root->right = newNode(3);
    root->left->left = newNode(4);
    root->left->right = newNode(5);

    printf("Height of the tree is %d\n", height(root));

    struct Node* root2 = newNode(1);
    root2->right = newNode(2);
    root2->right->right = newNode(3);
    root2->right->right->right = newNode(4);

    printf("Height of the second tree is %d\n", height(root2));

    return 0;
}


---

How to Compile and Run

Using GCC

1. Save the file as tree_height.c
2. Open terminal or command prompt
3. Compile:

bash
gcc tree_height.c -o tree_height


4. Run:

bash
./tree_height


(On Windows, use tree_height.exe)

---

Sample Output


Height of the tree is 2
Height of the second tree is 3


---

 How the Algorithm Works

1. If node is NULL → return -1
2. Recursively compute:

   * Height of left subtree
   * Height of right subtree
3. Return:


max(leftHeight, rightHeight) + 1


---

Time and Space Complexity

| Complexity Type  | Value |
| ---------------- | ----- |
| Time Complexity  | O(n)  |
| Space Complexity | O(h)  |

Where:

* *n* = number of nodes
* *h* = height of tree (recursive stack space)

---

Concepts Covered

* Binary Trees
* Recursion
* Tree Height Calculation
* Dynamic Memory Allocation
* Tree Traversal Logic

---

Possible Improvements

* Add user input to build tree
* Add level-order height calculation
* Add tree traversal functions (Inorder, Preorder, Postorder)
* Convert to menu-driven program
* Free allocated memory properly

---
