## Pseudocode:
```
procedure quickSort(A: list of sortable items, low: starting index, high: ending index)
    if low < high
        pi = partition(A, low, high)
        quickSort(A, low, pi - 1)
        quickSort(A, pi + 1, high)

procedure partition(A: list of sortable items, low: starting index, high: ending index) : index
    pivot = A[high]  // Choose the last element as the pivot
    i = low - 1     // Index of the smaller element
    for j from low to high - 1
        if A[j] < pivot
            i = i + 1
            swap A[i] with A[j]
    swap A[i + 1] with A[high] // Place the pivot element in its correct position
    return i + 1

A: Array to be sorted
low: Starting index of the array
high: Ending index of the array
pi: Pivot index
i, j: Loop indices

```

## Algorithm:
```c
#include <stdio.h>

void swap(int* a, int* b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

int partition(int arr[], int low, int high) {
    int pivot = arr[high];
    int i = low - 1;

    for (int j = low; j < high; j++) {
        if (arr[j] < pivot) {
            i++;
            swap(&arr[i], &arr[j]);
        }
    }

    swap(&arr[i + 1], &arr[high]);
    return i + 1;
}

void quickSort(int arr[], int low, int high) {
    if (low < high) {
        int pi = partition(arr, low, high);

        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}
```

### Explanation:

1. Quick Sort follows the divide and conquer paradigm.
2. It chooses a pivot element and partitions the array around the pivot, such that elements smaller than the pivot go to the left and larger go to the right.
3. It then recursively applies this process to the left and right subarrays until the entire array is sorted.
# Other Info:
### When to Use Quick Sort:

- Quick Sort is suitable for a wide range of input data sizes.
- Often used as a general-purpose, in-place sorting algorithm.
- Preferred over other sorting algorithms when average time complexity and low space complexity are required.

### Time Complexity:

- **Worst Case:** O(n^2) comparisons and swaps (rare, occurs when the pivot is always the smallest or largest element).
- **Average Case:** O(n log n)
- **Best Case:** O(n log n) comparisons and O(log n) swaps (when the pivot divides the array into nearly equal halves).

### Space Complexity:

- Quick Sort has a space complexity of O(log n) due to the recursive calls and partitioning.