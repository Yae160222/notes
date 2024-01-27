# AVL Tree (Balanced [[Binary Search Tree|BST]]):
1. An AVL tree is a self-balancing binary search tree (BST) where the height of the left and right subtrees of any node differs by at most one (the balance factor). 
2. It is named after its inventors, Adelson-Velsky and Landis.
### Properties of AVL Trees:

1. **Balanced Property**: For every node in the AVL tree, the height of the left and right subtrees can differ by at most 1.
    
2. **Balance Factor**: The balance factor of a node is the difference in height between the left and right subtrees. It can be -1, 0, or 1 for an AVL tree.
### AVL Tree Rotations:

To maintain the AVL property during insertions and deletions, four types of rotations are performed:

- **Left Rotation**
- **Right Rotation**
- **Left-Right Rotation**
- **Right-Left Rotation**
### Time Complexity:

- **Insertion**: O(log n)
- **Deletion**: O(log n)
- **Searching**: O(log n)

# Functions
### **Creating a Node: `createNode`**

This function creates a new node for the AVL tree with the given data.
```c
typedef struct AVLNode {
    int data;
    int height;  // Height of the subtree rooted at this node
    struct AVLNode* left;
    struct AVLNode* right;
} AVLNode;

AVLNode* createNode(int data) {
    AVLNode* newNode = (AVLNode*)malloc(sizeof(AVLNode));
    if (newNode == NULL) {
        fprintf(stderr, "Memory error\n");
        exit(EXIT_FAILURE);
    }

    newNode->data = data;
    newNode->height = 1;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

```
### **Calculating Balance Factor: `getBalance`**

This function calculates the balance factor for a node (difference in height between left and right subtrees).
```c
int getBalance(AVLNode* node) {
    if (node == NULL)
        return 0;
    return getHeight(node->left) - getHeight(node->right);
}

```
### **Updating the Height: `updateHeight`**

This function updates the height of a node based on the heights of its children.
```c
void updateHeight(AVLNode* node) {
    int leftHeight = getHeight(node->left);
    int rightHeight = getHeight(node->right);
    node->height = (leftHeight > rightHeight ? leftHeight : rightHeight) + 1;
}

```
### **Rotations: Left Rotation and Right Rotation**

Rotations are crucial operations in AVL trees to maintain the balance factor and the AVL property.
**Left rotation**
```c
AVLNode* leftRotate(AVLNode* y) {
    AVLNode* x = y->right;
    AVLNode* T2 = x->left;

    // Perform rotation
    x->left = y;
    y->right = T2;

    // Update heights
    updateHeight(y);
    updateHeight(x);

    return x;
}

```
**Right rotation**
```c
AVLNode* rightRotate(AVLNode* x) {
    AVLNode* y = x->left;
    AVLNode* T2 = y->right;

    // Perform rotation
    y->right = x;
    x->left = T2;

    // Update heights
    updateHeight(x);
    updateHeight(y);

    return y;
}

```
### **Double Rotations: Left-Right Rotation and Right-Left Rotation**

Double rotations are used when a node violates the AVL property and needs a combination of rotations.
**Left-Right Rotation**
```c
AVLNode* leftRightRotate(AVLNode* z) {
    z->left = leftRotate(z->left);
    return rightRotate(z);
}

```
**Right-Left Rotation**
```c
AVLNode* rightLeftRotate(AVLNode* z) {
    z->right = rightRotate(z->right);
    return leftRotate(z);
}

```

### **Inserting a Node: `insertNode`**

This function inserts a new node with the given data into the AVL tree and performs necessary rotations to maintain the AVL property.
```c
AVLNode* insertNode(AVLNode* root, int data) {
    if (root == NULL)
        return createNode(data);

    if (data < root->data)
        root->left = insertNode(root->left, data);
    else if (data > root->data)
        root->right = insertNode(root->right, data);
    else
        return root; // Duplicate keys not allowed

    // Update height of the current node
    updateHeight(root);

    // Check balance and perform rotations
    int balance = getBalance(root);

    // Left Heavy
    if (balance > 1) {
        if (data < root->left->data)
            return rightRotate(root); // Left-Left case
        else
            return leftRightRotate(root); // Left-Right case
    }

    // Right Heavy
    if (balance < -1) {
        if (data > root->right->data)
            return leftRotate(root); // Right-Right case
        else
            return rightLeftRotate(root); // Right-Left case
    }

    return root; // No rotations needed
}

```
### **Deleting a node:** `deleteNode`
Deleting a node in an AVL tree involves finding and removing the node while maintaining the AVL balance property by performing rotations.
```c
AVLNode* deleteNode(AVLNode* root, int data) {
    if (root == NULL)
        return root;

    if (data < root->data)
        root->left = deleteNode(root->left, data);
    else if (data > root->data)
        root->right = deleteNode(root->right, data);
    else {
        // Node to be deleted found

        // Case 1: Node with only one child or no child
        if (root->left == NULL) {
            AVLNode* temp = root->right;
            free(root);
            return temp;
        } else if (root->right == NULL) {
            AVLNode* temp = root->left;
            free(root);
            return temp;
        }

        // Case 3: Node with two children
        AVLNode* temp = findMin(root->right);
        root->data = temp->data;
        root->right = deleteNode(root->right, temp->data);
    }

    // Update height of the current node
    updateHeight(root);

    // Check balance and perform rotations
    int balance = getBalance(root);

    // Left Heavy
    if (balance > 1) {
        if (getBalance(root->left) >= 0)
            return rightRotate(root); // Left-Left case
        else
            return leftRightRotate(root); // Left-Right case
    }

    // Right Heavy
    if (balance < -1) {
        if (getBalance(root->right) <= 0)
            return leftRotate(root); // Right-Right case
        else
            return rightLeftRotate(root); // Right-Left case
    }

    return root; // No rotations needed
}

```