# Functions:
### **Heapify Up (or Bubble Up)**:

- This function is used to maintain the min heap property after inserting an element.
```c
void heapifyUp(int arr[], int index) {
    int temp = arr[index];
    while (index > 0 && temp < arr[(index - 1) / 2]) {
        arr[index] = arr[(index - 1) / 2];
        index = (index - 1) / 2;
    }
    arr[index] = temp;
}

```

### **Heapify Down (or Trickle Down)**:

- This function is used to maintain the min heap property after removing the root (or any element).
```c
void heapifyDown(int arr[], int size, int index) {
    int smallest = index;
    int left = 2 * index + 1;
    int right = 2 * index + 2;

    if (left < size && arr[left] < arr[smallest])
        smallest = left;

    if (right < size && arr[right] < arr[smallest])
        smallest = right;

    if (smallest != index) {
        int temp = arr[index];
        arr[index] = arr[smallest];
        arr[smallest] = temp;
        heapifyDown(arr, size, smallest);
    }
}

```

### **Insert**:

- This function inserts a new element into the min heap.
```c
void insert(int arr[], int* size, int value) {
    (*size)++;
    arr[*size - 1] = value;
    heapifyUp(arr, *size - 1);
}

```

### **Delete Root**:

- This function removes the root element (minimum) from the min heap.
```c
int deleteRoot(int arr[], int* size) {
    if (*size == 0)
        return -1;  // Heap is empty

    int root = arr[0];
    arr[0] = arr[*size - 1];
    (*size)--;
    heapifyDown(arr, *size, 0);

    return root;
}

```

**Build Heap**:

- This function builds a min heap from an array of elements.
```c
void buildHeap(int arr[], int size) {
    for (int i = size / 2 - 1; i >= 0; i--)
        heapifyDown(arr, size, i);
}

```