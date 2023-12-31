# 总结
平均时间复杂度O(nlogn) \
最坏时间复杂度O($n^2$) \
空间复杂度O(logn) \
不稳定 


![9278660b5cc0050f28f4d063b1cc1fa](https://github.com/zdong2080/Kais-LC-Garden/assets/85309696/0eba45ac-395c-466b-afe6-1a4a05b7dca8)

``` java
import java.util.Random;

public class QuickSort {

    private static void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }

    private static int partition(int[] arr, int low, int high) {
        Random rand = new Random();
        int pivotIndex = low + rand.nextInt(high - low + 1);
        int pivot = arr[pivotIndex];
        swap(arr, pivotIndex, high);  // Move pivot to end
        int i = low - 1;  // Index of smaller element

        for (int j = low; j <= high - 1; j++) {
            if (arr[j] < pivot) {
                i++;
                swap(arr, i, j);
            }
        }
        swap(arr, i + 1, high);  // Swap pivot back into correct position
        return i + 1;  // Return pivot index
    }

    private static void quickSort(int[] arr, int low, int high) {
        if (low < high) {
            int pi = partition(arr, low, high);
            quickSort(arr, low, pi - 1);
            quickSort(arr, pi + 1, high);
        }
    }

    public static void sort(int[] arr) {
        quickSort(arr, 0, arr.length - 1);
    }

    // Testing the implementation
    public static void main(String[] args) {
        int[] data = { 9, -3, 5, 2, 6, 8, -6, 1, 3 };
        sort(data);
        for (int i = 0; i < data.length; i++) {
            System.out.print(data[i] + " ");
        }
    }
}

```
