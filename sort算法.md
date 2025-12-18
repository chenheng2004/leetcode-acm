# 快速排序
```
import java.util.ArrayList;

// import javafx.beans.binding.IntegerExpression;
// 分治思想 时间复杂度 O(nlogn) ,空间复杂度O(logn),
public class QuickSort {
    public static void quickSort(int[] arr, int left, int right) {
        if (left < right) {
            int pivotIndex = partition(arr, left, right);
            quickSort(arr, left, pivotIndex - 1);
            quickSort(arr, pivotIndex + 1, right);
        }
    }

    private static int partition(int[] arr, int left, int right) {
        int base = arr[left];//选择left作为基准数字
        while(left<right) {
            //选择了left作为基准，从右往左开始找小于base的数字，如果找到则交换right到left的位置
            while(left < right && arr[right] >= base){
                right--;
            }
            arr[left] = arr[right];
            // 选择了left作为基准，从左往右开始找大于base的数字，如果找到则交换left到right的位置
            while(left < right && arr[left] <= base){
                left++;
            }
            arr[right] = arr[left];       
        }
        // 将base交换到left的位置,按照基准数字将数组分成两部分，左边小于base，右边大于base
        arr[left] = base;
        printArray(arr);
        // 返回基准数字的位置，用于分治法
        return left;
    }

    public static void main(String[] args) {
        int[] arr = {8, 4, 2, 9, 5, 6, 1, 3, 7};
        System.out.println("排序前：");
        printArray(arr);

        quickSort(arr, 0, arr.length - 1);

        System.out.println("排序后：");
        printArray(arr);
    }

    private static void printArray(int[] arr) {
        for (int num : arr) {
            System.out.print(num + " ");
        }
        System.out.println();
    }
}

```
