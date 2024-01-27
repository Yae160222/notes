## Pseudocode:
```
procedure insertionSort(A: list of sortable items)
    n = length(A)
    for i from 1 to n
        key = A[i]
        j = i - 1
        while j >= 0 and A[j] > key
            A[j + 1] = A[j]
            j = j - 1
        A[j + 1] = key

A: Array to be sorted
n: Number of elements in the array
i, j: Loop indices
key: Element being compared and moved

```

## Algorithm:
```c
#include <stdio.h>

void insertionSort(int arr[], int n) {
    int i, j, key;
    for (i = 1; i < n; i++) {
        key = arr[i];
        j = i - 1;

        // Move elements of arr[0..i-1] that are greater than key
        // to one position ahead of their current position
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j = j - 1;
        }
        arr[j + 1] = key;
    }
}
```
### Explanation:

1. The algorithm divides the array into a sorted and an unsorted region.
2. It iterates through the array, considering one element at a time from the unsorted region.
3. For each element, it compares it with the elements in the sorted region and shifts larger elements to the right to make space for the element to be inserted.
4. It repeats this process until the entire array is sorted.
# Other Info:
### When to Use Insertion Sort:

- Insertion Sort is suitable for small datasets or nearly sorted datasets.
- Often used in practice for its simplicity and low overhead.
- Efficient for very small datasets or when the dataset is almost sorted.
### Time Complexity:

- **Worst Case:** O(n^2) comparisons and swaps (when the array is in reverse order).
- **Average Case:** O(n^2) comparisons and swaps.
- **Best Case:** O(n) comparisons and O(1) swaps (when the array is already sorted).

### Space Complexity:

- Insertion Sort is an in-place sorting algorithm, meaning it sorts the elements within the original array without using additional memory except for a few variables.