## Problem Statement:
Given an array, arr[]. Sort the array using insertion sort algorithm.

### Code (Iterative Soln):
```
class Solution {

    //divide the array into sorted and unsorted sections
    //In each iteration, the algorithm picks one element ("key") and inserts it into its correct position in the sorted part of the array.
    //the inner while loop basically shifts the elements using swapping
    //j-- ensures we continue shifting until we find correct position for arr[j]
    //STABLE : equal elements are never swapped out of order
    //Tc:O(n^2) wc ac, O(n) bc -> no swaps, inner loop doesn't run; Sc:O(1)

    public void insertionSort(int arr[]) {
        int n = arr.length;
        for (int i = 0; i < n; i++) {
            int j = i;
            while (j > 0 && arr[j - 1] > arr[j]) {
                int temp = arr[j - 1];
                arr[j - 1] = arr[j];
                arr[j] = temp;
                j--;
            }
        }
    }
}
```

### Code (Recursive Soln):
```
class Solution {

    //recursive
    //Tc: BestCase:O(N) worst&avg:O(N^2) Sc:O(N) no comparision needed, only one comparision per recc call

    public void insertionSort(int arr[]) {
        insertionSortRecursive(arr, 1, arr.length);
    }
    static void insertionSortRecursive(int[] arr, int i, int n) {
        if (i == n) return;                  // Base case: Entire array sorted
        int key = arr[i];
        int j = i - 1;
        while (j >= 0 && arr[j] > key) {     // Move elements that are greater than `key` one position ahead
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;                    // Insert the key at the correct position
        insertionSortRecursive(arr, i + 1, n);   // Recursive call for the next element
    }
}
```