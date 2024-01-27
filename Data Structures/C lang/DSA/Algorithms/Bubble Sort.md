## Pseudocode:
```
procedure bubbleSort(A: list of sortable items)
    n = length(A)
    for i from 0 to n - 1
        for j from 0 to n - i - 1
            if A[j] > A[j + 1]
                swap A[j] with A[j + 1]

A: Array to be sorted
n: Number of elements in the array
i, j: Loop indices

```

## Explanation:
1. Start with the first element (index 0) and compare it with the next element (index 1).
2. If the first element is greater than the next element, swap them.
3. Move to the next pair of elements and repeat the comparison and swapping process until the end of the array.
4. After the first pass, the largest element "bubbles up" to the end of the array.
5. Repeat the above steps for each subsequent element (excluding the already sorted ones) until the array is sorted.
## Algorithm:
```c
#include <stdio.h>

void bubbleSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            // If the current element is larger than the next element, swap them
            if (arr[j] > arr[j + 1]) {
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}
```

# Other Info:
### Time Complexity:

- **Worst Case:** O(n^2) comparisons and swaps (when the array is in reverse order).
- **Average Case:** O(n^2) comparisons and swaps.
- **Best Case:** O(n) comparisons and O(1) swaps (when the array is already sorted).

### Space Complexity:

- Bubble Sort is an in-place sorting algorithm, meaning it sorts the elements within the original array without using additional memory except for a few variables.

### Advantages:

- Simple and easy to implement.
- Minimal space complexity since it sorts in-place.
- Stable sorting algorithm (keeps the order of equal elements).
- No additional memory required except for a few variables

### Disadvantages:

- Very inefficient for large datasets due to its O(n^2) time complexity.