## Pseudocode:
```c
procedure selectionSort(A: list of sortable items)
    n = length(A)
    for i from 0 to n - 1
        minIndex = i
        for j from i + 1 to n
            if A[j] < A[minIndex]
                minIndex = j
        swap A[i] with A[minIndex]

A: Array to be sorted
n: Number of elements in the array
i, j: Loop indices
minIndex: Index of the minimum element found so far

```

## Algorithm:
```c
#include <stdio.h>

void selectionSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        int minIndex = i;
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[minIndex])
                minIndex = j;
        }
        // Swap the found minimum element with the first unsorted element
        int temp = arr[minIndex];
        arr[minIndex] = arr[i];
        arr[i] = temp;
    }
}
```
### Explanation:

1. Selection Sort divides the array into a sorted and an unsorted region.
2. In each iteration, it finds the minimum element from the unsorted region.
3. It then swaps the minimum element with the first unsorted element, effectively extending the sorted region.
4. Repeat these steps until the entire array is sorted.
### When to Use Selection Sort:

- Selection Sort is suitable for small datasets or scenarios where the simplicity of the algorithm is more important than efficiency.
# Other Info:
### Time Complexity:

- **Worst Case:** O(n^2) comparisons and swaps (when the array is in reverse order).
- **Average Case:** O(n^2) comparisons and swaps.
- **Best Case:** O(n^2) comparisons and O(1) swaps (when the array is already sorted).
### Space Complexity:

- Selection Sort is an in-place sorting algorithm, meaning it sorts the elements within the original array without using additional memory except for a few variables.