## Pseudocode:
```
procedure mergeSort(A: list of sortable items)
    if length(A) <= 1
        return A
    mid = length(A) / 2
    left = mergeSort(A[0...mid-1])
    right = mergeSort(A[mid...length(A)-1])
    return merge(left, right)

procedure merge(left: list of sortable items, right: list of sortable items)
    result = []
    while left and right have elements
        if left[0] <= right[0]
            append left[0] to result
            remove first element from left
        else
            append right[0] to result
            remove first element from right
    append remaining elements of left and right to result
    return result

A: Array to be sorted
mid: Middle index of the array
left: Left half of the array
right: Right half of the array


```

## Algorithm:
```c
#include <stdio.h>
#include <stdlib.h>

void merge(int arr[], int left, int mid, int right) {
    int n1 = mid - left + 1;
    int n2 = right - mid;

    // Create temporary arrays
    int *L = (int *)malloc(n1 * sizeof(int));
    int *R = (int *)malloc(n2 * sizeof(int));

    // Copy data to temporary arrays L[] and R[]
    for (int i = 0; i < n1; i++)
        L[i] = arr[left + i];
    for (int j = 0; j < n2; j++)
        R[j] = arr[mid + 1 + j];

    // Merge the temporary arrays back into arr[left...right]
    int i = 0, j = 0, k = left;
    while (i < n1 && j < n2) {
        if (L[i] <= R[j]) {
            arr[k] = L[i];
            i++;
        } else {
            arr[k] = R[j];
            j++;
        }
        k++;
    }

    // Copy the remaining elements of L[], if any
    while (i < n1) {
        arr[k] = L[i];
        i++;
        k++;
    }

    // Copy the remaining elements of R[], if any
    while (j < n2) {
        arr[k] = R[j];
        j++;
        k++;
    }

    // Free temporary arrays
    free(L);
    free(R);
}

void mergeSort(int arr[], int left, int right) {
    if (left < right) {
        int mid = left + (right - left) / 2;

        // Sort first and second halves
        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);

        // Merge the sorted halves
        merge(arr, left, mid, right);
    }
}

```
### Explanation:

1. Merge Sort follows the divide and conquer paradigm.
2. It recursively divides the array into smaller subarrays until each subarray has a single element.
3. Then, it merges these subarrays in a sorted manner until a single sorted array is obtained.

# Other Info:
### When to Use Merge Sort:

- Merge Sort is suitable for a wide range of input data sizes.
- Ideal for scenarios where stability is important.
- Useful when an algorithm with guaranteed O(n log n) time complexity is required.

### Time Complexity:

- **Worst Case:** O(n log n)
- **Average Case:** O(n log n)
- **Best Case:** O(n log n)

### Space Complexity:

- Merge Sort has a space complexity of O(n) due to the need for temporary arrays.