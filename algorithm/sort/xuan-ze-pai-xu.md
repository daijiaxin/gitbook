# 选择排序

{% hint style="info" %}
**选择排序（Selection Sort）**：每次从未排序的部分中选择最小（或最大）的元素，并将其放置在已排序部分的末尾。
{% endhint %}

## 步骤

1. 从待排序的数组中找到最小（或最大）的元素。
2. 将该最小（或最大）元素与数组的第一个元素进行交换。
3. 在剩余的未排序部分中，找到最小（或最大）的元素，将其与数组的第二个元素进行交换。
4. 在剩余未排序部分中重复以上步骤，直到数组完全排序。

## 代码

```go
// Some code
package main

import "fmt"

func selectionSort(arr []int) {
    n := len(arr)
    for i := 0; i < n-1; i++ {
        // 找到未排序部分的最小元素索引
        minIndex := i
        for j := i + 1; j < n; j++ {
            if arr[j] < arr[minIndex] {
                minIndex = j
            }
        }
        // 将最小元素与未排序部分的第一个元素交换
        arr[i], arr[minIndex] = arr[minIndex], arr[i]
    }
}

func main() {
    arr := []int{64, 34, 25, 12, 22, 11, 90}
    selectionSort(arr)
    fmt.Println("排序结果:", arr)
}
```
