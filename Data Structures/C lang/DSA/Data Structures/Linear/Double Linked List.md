# Functions:
## **Create a Node**

- This function creates a new node with the given data and returns a pointer to the newly created node.
```c
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
    struct Node* prev;
};

struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    if (newNode == NULL) {
        perror("Memory allocation failed");
        exit(EXIT_FAILURE);
    }
    newNode->data = data;
    newNode->next = NULL;
    newNode->prev = NULL;
    return newNode;
}

```

## **Insert at the Beginning**

- This function inserts a new node with the given data at the beginning of the doubly linked list.
```c
void insertAtBeginning(struct Node** head, int data) {
    struct Node* newNode = createNode(data);
    if (*head == NULL) {
        *head = newNode;
        return;
    }

    newNode->next = *head;
    (*head)->prev = newNode;
    *head = newNode;
}

```

## **Insert at the End**

- This function inserts a new node with the given data at the end of the doubly linked list.
```c
void insertAtEnd(struct Node** head, int data) {
    struct Node* newNode = createNode(data);
    if (*head == NULL) {
        *head = newNode;
        return;
    }

    struct Node* temp = *head;
    while (temp->next != NULL) {
        temp = temp->next;
    }
    temp->next = newNode;
    newNode->prev = temp;
}

```



## **Delete Node**

- This function deletes a node with the given data from the doubly linked list.
```c
void deleteNode(struct Node** head, int data) {
    if (*head == NULL)
        return;

    struct Node* temp = *head;

    // Find the node to be deleted
    while (temp != NULL && temp->data != data) {
        temp = temp->next;
    }

    // If the node is not found
    if (temp == NULL)
        return;

    // Update the next of the previous node
    if (temp->prev != NULL)
        temp->prev->next = temp->next;

    // Update the previous of the next node
    if (temp->next != NULL)
        temp->next->prev = temp->prev;

    // Update the head if needed
    if (*head == temp)
        *head = temp->next;

    free(temp);
}

```
## **Display List Forward**

- This function displays the elements of the doubly linked list in forward order.
```c
void displayListForward(struct Node* head) {
    struct Node* temp = head;
    while (temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->next;
    }
    printf("NULL\n");
}

```

## **Display List Backward**

- This function displays the elements of the doubly linked list in backward order.
```c
void displayListBackward(struct Node* head) {
    if (head == NULL)
        return;

    struct Node* temp = head;

    // Move to the end of the list
    while (temp->next != NULL) {
        temp = temp->next;
    }

    // Traverse in reverse order
    while (temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->prev;
    }
    printf("NULL\n");
}

```

## **Free List**

- This function frees the memory allocated for the doubly linked list.
```c
void freeList(struct Node* head) {
    struct Node* temp;
    while (head != NULL) {
        temp = head;
        head = head->next;
        free(temp);
    }
}

```