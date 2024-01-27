# Defination:
Here the nodes are linked with only single link. 
Current Nodes contains link or [[Pointer|pointer]] to the next node

# Functions and implementations:
## **Create a node**
 This function creates a new node with the given data and returns a pointer to the newly created node
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

- This function inserts a new node with the given data at the beginning of the linked list.

```c
void insertAtBeginning(struct Node** head, int data) {
    struct Node* newNode = createNode(data);
    newNode->next = *head;
    *head = newNode;
}
```

## **Insert at the End**

- This function inserts a new node with the given data at the end of the linked list

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
}
  ```
## **Delete Node**

- This function deletes a node with the given data from the linked list.
   
 ```c
 void deleteNode(struct Node** head, int data) {
    if (*head == NULL)
        return;

    struct Node* temp = *head;
    struct Node* prev = NULL;

    if (temp->data == data) {
        *head = temp->next;
        free(temp);
        return;
    }

    while (temp != NULL && temp->data != data) {
        prev = temp;
        temp = temp->next;
    }

    if (temp == NULL)
        return;

    prev->next = temp->next;
    free(temp);
}

```


## **Display List**

- This function displays the elements of the linked list.

```c
void displayList(struct Node* head) {
    struct Node* temp = head;
    while (temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->next;
    }
    printf("NULL\n");
}
```



## **Free List**

- This function frees the memory allocated for the linked list.
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