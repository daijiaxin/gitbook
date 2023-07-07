# 冒泡排序

{% hint style="info" %}
**冒泡排序（Bubble Sort）**：重复比较相邻的两个元素，并交换位置，直到整个数组按照升序或降序排列。
{% endhint %}

## 步骤

1. 从数组的第一个元素开始，依次比较相邻的两个元素。
2. 如果顺序不正确（例如，当前元素比下一个元素大），则交换它们的位置。
3. 继续向数组的下一个位置移动，并重复步骤1和步骤2，直到完成一轮的比较。
4. 一轮比较后，最大（或最小）的元素会被放置在数组的末尾。
5. 重复进行步骤1至步骤4，但每次比较的元素个数减少一位，直到所有元素都按照升序或降序排列。

## 代码实现

```go
// Some code
package main

import "fmt"

func bubbleSort(arr []int) {
    n := len(arr)
    for i := 0; i < n-1; i++ {
        // 执行一轮比较
        for j := 0; j < n-i-1; j++ {
            // 如果顺序不正确，则交换位置
            if arr[j] > arr[j+1] {
                arr[j], arr[j+1] = arr[j+1], arr[j]
            }
        }
    }
}

func main() {
    arr := []int{64, 34, 25, 12, 22, 11, 90}
    bubbleSort(arr)
    fmt.Println("排序结果:", arr)
}
```
