## Problem Statement:
Given an array, arr[]. Sort the array using bubble sort algorithm.

### Code (Iterative Soln):
```
class Solution {

    //in each pass, larger elements "bubble" up to their correct position at the end of the list
    //repeatedly swaps adjacent elements if they are in wrong order
    //after each iteration: largest element moves to the correct position
    //outer loop runs in reverse order, n-1 to 0 [0 not included, bcs sigle ele is always sorted]
    //STABLE: only adjacent swaps are made, equal elements are never swapped 
    //Tc: wc-O(n^2) [reverse sorted], bc-O(n) [already sorted] ; Sc:O(1)

    public static void bubbleSort(int arr[]) {
        int n = arr.length;
        for(int i = n-1; i > 0; i--){
            boolean swapped = false; //to check if array is already sorted
            for(int j = 0; j < i; j++){
                if(arr[j] > arr[j+1]){
                    int temp = arr[j];
                    arr[j] = arr[j+1];
                    arr[j+1] = temp;
                    
                    swapped = true;
                }
            }
            if(!swapped) break;
        }
    }
}
```

### Code (Recursive Soln):
```
class Solution {

    //recursive soln
    //Tc:O(N^2) Sc:O(n)

    public static void bubbleSort(int arr[]) {
        int n = arr.length;
        bubbleSortHelper(arr, n);
    }
    static void bubbleSortHelper(int[] arr, int n) {
        if (n == 1) return;//base case
        for (int j = 0; j <= n - 2; j++) {
            if (arr[j] > arr[j + 1]) {
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
        bubbleSortHelper(arr, n - 1);    //Range reduced after recursion
    }
}
```