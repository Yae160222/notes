# Binary Search Tree(BST):
A Binary Search Tree (BST) is a [[Binary Tree|binary tree]] that maintains the following property:

- For any given node in the tree, all nodes in the left subtree have values less than the node's value, and all nodes in the right subtree have values greater than the node's value
### Properties of Binary Search Trees:

1. **Binary Tree Structure**: Each node can have at most two children: a left child and a right child.
    
2. **Binary Search Property**: For any node `n`, all nodes in the left subtree of `n` have values less than `n`, and all nodes in the right subtree have values greater than `n`.
### Time Complexity (Average):

- **Insertion**: O(log n)
- **Deletion**: O(log n)
- **Searching**: O(log n)
- **Note:** If the tree is heavily unbalanced time complexity increases to O(n).


# Function
### **Creating a Node: `createNode`**

This function creates a new node for the BST with the given data.
```c
TreeNode* createNode(int data) {
    TreeNode* newNode = (TreeNode*)malloc(sizeof(TreeNode));
    if (newNode == NULL) {
        fprintf(stderr, "Memory error\n");
        exit(EXIT_FAILURE);
    }

    newNode->data = data;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

```
### **Inserting a Node: `insertNode`**

This function inserts a new node with the given data into the BST.
```c
TreeNode* insertNode(TreeNode* root, int data) {
    if (root == NULL)
        return createNode(data);

    if (data < root->data)
        root->left = insertNode(root->left, data);
    else if (data > root->data)
        root->right = insertNode(root->right, data);

    return root;
}

```
### **Searching for a Node: `searchNode`**

This function searches for a node with a given key in the BST.
```c
TreeNode* searchNode(TreeNode* root, int key) {
    if (root == NULL || root->data == key)
        return root;

    if (key < root->data)
        return searchNode(root->left, key);

    return searchNode(root->right, key);
}

```
### **Deleting a Node: `deleteNode`**

This function deletes a node with the given key from the BST.
```c
TreeNode* deleteNode(TreeNode* root, int key) {
    if (root == NULL)
        return root;

    if (key < root->data)
        root->left = deleteNode(root->left, key);
    else if (key > root->data)
        root->right = deleteNode(root->right, key);
    else {
        // Node to be deleted found

        // Case 1: Node with only one child or no child
        if (root->left == NULL) {
            TreeNode* temp = root->right;
            free(root);
            return temp;
        } else if (root->right == NULL) {
            TreeNode* temp = root->left;
            free(root);
            return temp;
        }

        // Case 3: Node with two children
        TreeNode* temp = findMin(root->right);
        root->data = temp->data;
        root->right = deleteNode(root->right, temp->data);
    }
    return root;
}

```
### **Finding Minimum Node: `findMin`**

This function finds the node with the minimum value in a subtree.
```c
TreeNode* findMin(TreeNode* node) {
    while (node->left != NULL)
        node = node->left;
    return node;
}

```

### **Finding Maximum Node: `findMax`**

This function finds the node with the maximum value in a subtree
```c
TreeNode* findMax(TreeNode* node) {
    while (node->right != NULL)
        node = node->right;
    return node;
}

```
### **Deleting the Entire Tree: `deleteTree`**

This function deletes the entire binary search tree (BST), freeing all allocated memory
```c
void deleteTree(TreeNode* root) {
    if (root == NULL)
        return;

    deleteTree(root->left);
    deleteTree(root->right);
    free(root);
}

```