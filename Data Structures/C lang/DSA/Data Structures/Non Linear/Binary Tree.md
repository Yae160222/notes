# Types
1. ### **Full Binary Tree:**
    
    - A binary tree in which every node has either 0 or 2 children.
2. ### **Complete Binary Tree:**
    
    - A binary tree in which all levels are completely filled except possibly for the last level, which is filled from left to right.
3. ### **Perfect Binary Tree:**
    
    - A binary tree in which all internal nodes have exactly two children, and all leaf nodes are at the same level.
4. ### **Degenerate (or pathological) Tree:**
    
    - A binary tree in which each parent node has only one child (either left child or right child), making it essentially a linked list.
5. ### **Balanced Binary Tree:**
    
    - A binary tree in which the depth of the two subtrees of every node never differs by more than one. It ensures efficient performance for operations like searching, insertion, and deletion.
6. ### **Height-Balanced Tree:**
    
    - A binary tree in which the height of the left and right subtrees of any node differs by at most one.
7. ### **Skewed Binary Tree:**
    
    - A binary tree in which all the nodes are either right-skewed or left-skewed, resembling a linked list.
8. ### **Threaded Binary Tree:**
    
    - A binary tree in which every node has either a thread to its next inorder successor or a null right child.
9. ### **Expression Tree:**

    - A binary tree typically used to represent mathematical expressions, where the leaves are operands and the internal nodes are operators.

# Functions
### **Creating a Node: **`createNode`

This function creates a new node for the binary tree with the given data.
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

### **Inserting a Node: **`insertLevelOrder`

This function inserts a new node with the given data into the binary tree level wise.
Here [[Queue|queues]] are used
```c
struct TreeNode* insertLevelOrder(struct TreeNode* root, int value) {
    struct TreeNode* newNode = createNode(value);

    if (root == NULL) {
        root = newNode;
        return root;
    }

    struct TreeNode* queue[1000];
    int front = -1, rear = -1;
    queue[++rear] = root;

    while (front < rear) {
        struct TreeNode* current = queue[++front];

        if (current->left == NULL) {
            current->left = newNode;
            return root;
        } else {
            queue[++rear] = current->left;
        }

        if (current->right == NULL) {
            current->right = newNode;
            return root;
        } else {
            queue[++rear] = current->right;
        }
    }

    return root;
}

```

### **Deleting a Node: ** `deleteNode`

This function deletes a node with the given data from the binary tree.
```c
TreeNode* deleteNode(TreeNode* root, int data) {
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
### **Deleting the Entire Tree: `deleteTree`**

This function deletes the entire binary tree, freeing all allocated memory.
```c
void deleteTree(TreeNode* root) {
    if (root == NULL)
        return;

    deleteTree(root->left);
    deleteTree(root->right);
    free(root);
}

```