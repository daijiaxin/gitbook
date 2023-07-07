# 插入排序

{% hint style="info" %}
**插入排序（Insertion Sort）**：将数组分为已排序和未排序两部分，逐个将未排序的元素插入到已排序的部分的正确位置。
{% endhint %}

## 步骤

1. 将数组划分为已排序部分和未排序部分。初始时，已排序部分只包含第一个元素，而剩余的元素属于未排序部分。
2. 从未排序部分中取出第一个元素，将其插入到已排序部分的正确位置，使已排序部分仍然有序。
3. 重复步骤2，直到未排序部分为空，即所有元素都被插入到已排序部分。

```go
// Some code
package main

import "fmt"

func insertionSort(arr []int) {
    n := len(arr)
    for i := 1; i < n; i++ {
        key := arr[i]
        j := i - 1
        // 将比 key 大的元素向右移动
        for j >= 0 && arr[j] > key {
            arr[j+1] = arr[j]
            j--
        }
        arr[j+1] = key
    }
}

func main() {
    arr := []int{64, 34, 25, 12, 22, 11, 90}
    insertionSort(arr)
    fmt.Println("排序结果:", arr)
}
```
