# Red-Black Tree (Self-Balancing [[Binary Search Tree|BST]]):
1.  It is a [[Binary Search Tree|BST]] which uses a set of rules to maintain the balance.
2. It's named "red-black" because each node in the tree is assigned a color either red or black, and the tree satisfies specific properties related to these colors.

### Properties of Red-Black Trees:

1. **Color Property**: Each node is colored, either red or black.
    
2. **Root Property**: The root is black.
    
3. **Leaf Property**: All leaves (null or NIL nodes) are black.
    
4. **Red Node Property**: Both children of a red node are black.
    
5. **Black Depth Property**: For each node, any simple path from this node to any of its descendant leaves has the same black depth (the number of black nodes).

### Time Complexity (Worst Case):

- **Insertion**: O(log n)
- **Deletion**: O(log n)
- **Searching**: O(log n)
- **Note:** It is always O(log n)
# Functions:
### **Creating a Node: `createNode`**
```c
#include <stdlib.h>

typedef enum Color {
    RED,
    BLACK
} Color;

typedef struct Node {
    int data;
    Color color;
    struct Node* parent;
    struct Node* left;
    struct Node* right;
} Node;

Node* createNode(int data) {
    Node* newNode = (Node*)malloc(sizeof(Node));
    if (newNode == NULL) {
        fprintf(stderr, "Memory error\n");
        exit(EXIT_FAILURE);
    }

    newNode->data = data;
    newNode->color = RED;  // By default, new nodes are always red
    newNode->parent = NULL;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

```
### **Rotation Functions: Left Rotation and Right Rotation**
**Left Rotation**
```c
Node* leftRotate(Node* root, Node* x) {
    Node* y = x->right;
    x->right = y->left;

    if (y->left != NULL)
        y->left->parent = x;

    y->parent = x->parent;

    if (x->parent == NULL)
        root = y;
    else if (x == x->parent->left)
        x->parent->left = y;
    else
        x->parent->right = y;

    y->left = x;
    x->parent = y;

    return root;
}

```
**Right Rotation**
```c
Node* rightRotate(Node* root, Node* y) {
    Node* x = y->left;
    y->left = x->right;

    if (x->right != NULL)
        x->right->parent = y;

    x->parent = y->parent;

    if (y->parent == NULL)
        root = x;
    else if (y == y->parent->left)
        y->parent->left = x;
    else
        y->parent->right = x;

    x->right = y;
    y->parent = x;

    return root;
}

```
### **Fix Violations after Insertion: `fixInsertion`**
```c
void fixInsertion(Node** root, Node* pt) {
    Node* parent_pt = NULL;
    Node* grand_parent_pt = NULL;

    while ((pt != *root) && (pt->color == RED) && (pt->parent->color == RED)) {
        parent_pt = pt->parent;
        grand_parent_pt = pt->parent->parent;

        /* Case 1: Parent of pt is left child of Grandparent of pt */
        if (parent_pt == grand_parent_pt->left) {
            Node* uncle_pt = grand_parent_pt->right;

            /* Case 1a: Uncle is also red - only recoloring needed */
            if (uncle_pt != NULL && uncle_pt->color == RED) {
                grand_parent_pt->color = RED;
                parent_pt->color = BLACK;
                uncle_pt->color = BLACK;
                pt = grand_parent_pt;
            } else {
                /* Case 1b: pt is right child of its parent - left rotation needed */
                if (pt == parent_pt->right) {
                    *root = leftRotate(*root, parent_pt);
                    pt = parent_pt;
                    parent_pt = pt->parent;
                }

                /* Case 1c: pt is left child of its parent - right rotation needed */
                *root = rightRotate(*root, grand_parent_pt);
                swapColors(parent_pt, grand_parent_pt);
                pt = parent_pt;
            }
        } else { /* Case 2: Parent of pt is right child of Grandparent of pt */
            Node* uncle_pt = grand_parent_pt->left;

            /* Case 2a: Uncle is also red - only recoloring needed */
            if ((uncle_pt != NULL) && (uncle_pt->color == RED)) {
                grand_parent_pt->color = RED;
                parent_pt->color = BLACK;
                uncle_pt->color = BLACK;
                pt = grand_parent_pt;
            } else {
                /* Case 2b: pt is left child of its parent - right rotation needed */
                if (pt == parent_pt->left) {
                    *root = rightRotate(*root, parent_pt);
                    pt = parent_pt;
                    parent_pt = pt->parent;
                }

                /* Case 2c: pt is right child of its parent - left rotation needed */
                *root = leftRotate(*root, grand_parent_pt);
                swapColors(parent_pt, grand_parent_pt);
                pt = parent_pt;
            }
        }
    }

    (*root)->color = BLACK; // Ensure

```
### **Inserting a Node into Red-Black Tree: `insertNode`**
```c
Node* insertNode(Node* root, int data) {
    Node* pt = createNode(data);

    /* Standard BST insert */
    root = bstInsert(root, pt);

    /* Fix the tree after standard BST insert */
    fixInsertion(&root, pt);

    return root;
}

```
### **Fix Violations after Deletion: `fixDeletion`**
```c
void fixDeletion(Node** root, Node* x) {
    Node* w;
    while (x != *root && x->color == BLACK) {
        if (x == x->parent->left) {
            w = x->parent->right;
            if (w->color == RED) {
                w->color = BLACK;
                x->parent->color = RED;
                *root = leftRotate(*root, x->parent);
                w = x->parent->right;
            }
            if (w->left->color == BLACK && w->right->color == BLACK) {
                w->color = RED;
                x = x->parent;
            } else {
                if (w->right->color == BLACK) {
                    w->left->color = BLACK;
                    w->color = RED;
                    *root = rightRotate(*root, w);
                    w = x->parent->right;
                }
                w->color = x->parent->color;
                x->parent->color = BLACK;
                w->right->color = BLACK;
                *root = leftRotate(*root, x->parent);
                x = *root; // This will terminate the loop
            }
        } else {
            w = x->parent->left;
            if (w->color == RED) {
                w->color = BLACK;
                x->parent->color = RED;
                *root = rightRotate(*root, x->parent);
                w = x->parent->left;
            }
            if (w->right->color == BLACK && w->left->color == BLACK) {
                w->color = RED;
                x = x->parent;
            } else {
                if (w->left->color == BLACK) {
                    w->right->color = BLACK;
                    w->color = RED;
                    *root = leftRotate(*root, w);
                    w = x->parent->left;
                }
                w->color = x->parent->color;
                x->parent->color = BLACK;
                w->left->color = BLACK;
                *root = rightRotate(*root, x->parent);
                x = *root; // This will terminate the loop
            }
        }
    }
    x->color = BLACK;
}


```
### **Deleting a Node from Red-Black Tree: `deleteNode`**
```c
void deleteNode(Node** root, int key) {
    Node* z = bstSearch(*root, key);
    if (z == NULL) {
        printf("Node with key %d not found.\n", key);
        return;
    }

    Node* y = z;
    Color y_original_color = y->color;
    Node* x;

    if (z->left == NULL) {
        x = z->right;
        *root = rbTransplant(*root, z, z->right);
    } else if (z->right == NULL) {
        x = z->left;
        *root = rbTransplant(*root, z, z->left);
    } else {
        y = bstMinimum(z->right);
        y_original_color = y->color;
        x = y->right;
        if (y->parent == z)
            x->parent = y;
        else {
            *root = rbTransplant(*root, y, y->right);
            y->right = z->right;
            y->right->parent = y;
        }
        *root = rbTransplant(*root, z, y);
        y->left = z->left;
        y->left->parent = y;
        y->color = z->color;
    }

    if (y_original_color == BLACK)
        fixDeletion(root, x);
    free(z);
}

```
### **Deleting the Entire Red-Black Tree: `deleteTree`**
```c
void deleteTree(Node* root) {
    if (root == NULL)
        return;

    deleteTree(root->left);
    deleteTree(root->right);
    free(root);
}

```