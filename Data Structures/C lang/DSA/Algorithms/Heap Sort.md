## Pseudocode:
```
procedure heapify(arr: list of sortable items, n: number of items, i: index of the root)
    largest = i
    left_child = 2 * i + 1
    right_child = 2 * i + 2

    if left_child < n and arr[left_child] > arr[largest]
        largest = left_child

    if right_child < n and arr[right_child] > arr[largest]
        largest = right_child

    if largest != i
        swap arr[i] with arr[largest]
        heapify(arr, n, largest)

procedure heapSort(arr: list of sortable items, n: number of items)
    // Build max-heap
    for i from n/2 - 1 down to 0
        heapify(arr, n, i)

    // Extract elements one by one
    for i from n - 1 down to 1
        swap arr[0] with arr[i]
        heapify(arr, i, 0)

arr: Array to be sorted
n: Number of elements in the array
i, left_child, right_child: Loop indices and child indices
largest: Index of the largest element in a subtree

```

## Algorithm:
```c
#include <stdio.h>

void swap(int* a, int* b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

void heapify(int arr[], int n, int i) {
    int largest = i;
    int left_child = 2 * i + 1;
    int right_child = 2 * i + 2;

    if (left_child < n && arr[left_child] > arr[largest])
        largest = left_child;

    if (right_child < n && arr[right_child] > arr[largest])
        largest = right_child;

    if (largest != i) {
        swap(&arr[i], &arr[largest]);
        heapify(arr, n, largest);
    }
}

void heapSort(int arr[], int n) {
    // Build max-heap
    for (int i = n / 2 - 1; i >= 0; i--)
        heapify(arr, n, i);

    // Extract elements one by one
    for (int i = n - 1; i >= 1; i--) {
        swap(&arr[0], &arr[i]);
        heapify(arr, i, 0);
    }
}
```
### Explanation:

1. Heap Sort first builds a max-heap (or min-heap, depending on the desired order) from the input array.
2. It then repeatedly extracts the root element (the largest element in a max-heap or the smallest in a min-heap) and reconstructs the heap until the heap is empty.
3. This process results in a sorted array.
# Other Info:
### When to Use Heap Sort:

- Heap Sort is suitable for scenarios where a stable sorting algorithm is not needed.
- It's often used for sorting in-place.
- Efficient for sorting large datasets when stability is not a concern.

### Time Complexity:

- **Worst Case:** O(n log n)
- **Average Case:** O(n log n)
- **Best Case:** O(n log n)

### Space Complexity:

- Heap Sort has a space complexity of O(1) since it sorts the elements in-place.