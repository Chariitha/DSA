## Problem Statement:
Given an array arr[], its starting position l and its ending position r. Sort the array using the merge sort algorithm.

### Code:
```
class Solution {

    //divide and conquer algorithm: divides array into 2 equal parts and merge the sorted parts
    //merge() -> used to merge the 2 halves of the array (sorted) 
    //we use a temp array to merge
    //mergeSort -> divides into 2 parts, [low to mid] and [mid+1 to high]
    //we recursively split the array until ALL subarrays size becomes one
    //STABLE : when arr[left]<=arr[right] we prefer arr[left] so maintains relative order
    //Tc:O(N logN) Sc:O(N) -> {O(n) for temp array and O(log n) for recursion call stack}

    void merge(int arr[], int low, int mid, int high){
        ArrayList<Integer> temp = new ArrayList<>();    // temporary array
        int left = low;                                 // starting index of left half of arr
        int right = mid + 1;                            // starting index of right half of arr
       
        while (left <= mid && right <= high) {   //storing elements in the temporary array in a sorted manner 
            if (arr[left] <= arr[right]) {
                temp.add(arr[left]);
                left++;
            } else {
                temp.add(arr[right]);
                right++;
            }
        }
       
        while (left <= mid) {                // if elements on the left half are still left 
            temp.add(arr[left]);
            left++;
        }
        while (right <= high) {             //  if elements on the right half are still left 
            temp.add(arr[right]);
            right++;
        }
        
        for (int i = low; i <= high; i++) {   // transfering all elements from temporary to arr 
            arr[i] = temp.get(i - low);
        }
    }
    void MergeSort(int arr[], int low, int high){
        if (low >= high) return;
        int mid = (low + high) / 2 ;
        MergeSort(arr, low, mid);               // left half
        MergeSort(arr, mid + 1, high);          // right half
        merge(arr, low, mid, high);             // merging sorted halves
    }
    void mergeSort(int arr[], int l, int r) {
        MergeSort(arr, l, r);
    }
}
```