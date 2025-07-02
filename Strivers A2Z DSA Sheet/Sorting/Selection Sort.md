## Problem Statement:
Given an array arr, use selection sort to sort arr[] in increasing order.

### Code: 
```


class Solution {

    //In each pass, select smallest ele in the unsorted part and swap into its correct position
    //last ele is sorted, so loop till n-1
    //not STABLE : doesn't maintain the order for duplicate elements
    //Tc:O(n^2) Sc:O(1)

    void selectionSort(int[] arr) {
        int n = arr.length;
        for(int i = 0; i < n-1; i++){
            int minIndex = i;
            
            for(int j = i+1; j < n; j++){
                if(arr[j] < arr[minIndex]){
                    minIndex = j;
                }
            }
            
            if(minIndex != i){             //swap 
                int temp = arr[minIndex];
                arr[minIndex] = arr[i];
                arr[i] = temp;
            }
        }
    }
}
```