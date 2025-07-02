## Problem Statement:
Implement Quick Sort, a Divide and Conquer algorithm, to sort an array, arr[] in ascending order. Given an array, arr[], with starting index low and ending index high, complete the functions partition() and quickSort(). Use the last element as the pivot so that all elements less than or equal to the pivot come before it, and elements greater than the pivot follow it.

Note: The low and high are inclusive.

### Code: 
```
class Solution {

    // divide and conquer algorithm, but doesn't use extra array for sorting like merge sort, it only uses recursion stack space
    // in place sorting algorithm 
    //repetition of 2 steps
    //1. pick a pivot and place it in it's correct place in the sorted array
    //2. shift smaller elements to the left of the pivot and larger elements to the right
    //here we have chosen FIRST element as the pivot 
    //not STABLE
    //Tc:Avg case: O(N logN) {WC:O(n^2) if pivot selection is poor, happens when pivot is the smallest or largest element}
    //Sc:recursion stack space 
    //bc ac: O(N log n) -> if pivot divides array roughly in half each time     
    //wc: O(N) -> if pivot is smallest / largest ele everytime (already sorted array)

    static void quickSort(int arr[], int low, int high) {
        if(low<high){
            int p=partition(arr, low, high);
            quickSort(arr, low, p-1);
            quickSort(arr, p+1, high);
        }
    }
    static int partition(int arr[], int low, int high) {
        int pivot = arr[low];
        int i=low;
        int j=high;
        
        while(i<j){
            while(arr[i]<=pivot && i<=high-1){
                i++;
            }
            while(arr[j]>pivot && j>=low+1){
                j--;
            }
            if(i<j){
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }
        int temp = arr[low];
        arr[low] = arr[j];
        arr[j] = temp;
        
        return j;                   //return pivot index 
    }
}
```