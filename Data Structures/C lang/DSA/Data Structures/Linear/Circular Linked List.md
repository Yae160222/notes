# Functions:
## **Create a Node**

- This function creates a new node with the given data and returns a pointer to the newly created node.
```c
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    if (newNode == NULL) {
        perror("Memory allocation failed");
        exit(EXIT_FAILURE);
    }
    newNode->data = data;
    newNode->next = NULL;
    return newNode;
}

```
## **Insert at the Beginning**

- This function inserts a new node with the given data at the beginning of the circular linked list. 
```c
void insertAtBeginning(struct Node** head, int data) {
    struct Node* newNode = createNode(data);
    if (*head == NULL) {
        newNode->next = newNode;
        *head = newNode;
    } else {
        struct Node* last = (*head)->next;
        while (last->next != *head)
            last = last->next;

        last->next = newNode;
        newNode->next = *head;
        *head = newNode;
    }
}

```
## **Insert at the End**

- This function inserts a new node with the given data at the end of the circular linked list.
```c
void insertAtEnd(struct Node** head, int data) {
    struct Node* newNode = createNode(data);
    if (*head == NULL) {
        newNode->next = newNode;
        *head = newNode;
    } else {
        struct Node* last = (*head)->next;
        while (last->next != *head)
            last = last->next;

        last->next = newNode;
        newNode->next = *head;
    }
}

```
**Delete Node**

- This function deletes a node with the given data from the circular linked list.
```c
void deleteNode(struct Node** head, int data) {
    if (*head == NULL)
        return;

    struct Node* current = *head, *prev;

    // Find the node to be deleted
    while (current->data != data) {
        prev = current;
        current = current->next;

        // If we have traversed the entire list
        if (current == *head)
            return;
    }

    // If the node is the only node in the list
    if (current->next == *head) {
        *head = NULL;
    } else {
        // If the node is the first node
        if (current == *head) {
            while (prev->next != *head)
                prev = prev->next;
            *head = current->next;
            prev->next = *head;
        } else if (current->next == *head) {  // If the node is the last node
            prev->next = *head;
        } else {  // If the node is in the middle
            prev->next = current->next;
        }
    }

    free(current);
}

```
## **Display List**

- This function displays the elements of the circular linked list.
```c
void displayList(struct Node* head) {
    if (head == NULL)
        return;

    struct Node* temp = head;
    do {
        printf("%d -> ", temp->data);
        temp = temp->next;
    } while (temp != head);

    printf("...\n");
}

```
## **Free List**

- This function frees the memory allocated for the circular linked list.
```c
void freeList(struct Node* head) {
    if (head == NULL)
        return;

    struct Node* current = head;
    struct Node* temp;

    do {
        temp = current;
        current = current->next;
        free(temp);
    } while (current != head);
}

```