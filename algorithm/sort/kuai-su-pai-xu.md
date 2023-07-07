# 快速排序

{% hint style="info" %}
**快速排序（Quick Sort）**：通过选择一个基准元素，将数组分成两部分，一部分小于基准元素，另一部分大于基准元素，然后对两部分递归地进行排序。
{% endhint %}

## 步骤

1. 设定左指针 `left` 指向待排序数组的第一个元素，右指针 `right` 指向待排序数组的最后一个元素。
2. 选择一个基准元素 `pivot`，可以是第一个元素、最后一个元素或随机选择。
3. 将左指针 `left` 向右移动，直到找到一个大于基准元素的元素。
4. 将右指针 `right` 向左移动，直到找到一个小于基准元素的元素。
5. 如果左指针 `left` 小于等于右指针 `right`，则交换 `left` 和 `right` 指向的元素，并分别将左指针 `left` 和右指针 `right` 向后或向前移动一位。
6. 重复步骤3至步骤5，直到左指针 `left` 大于右指针 `right`。
7. 将基准元素 `pivot` 与左指针 `left` 指向的元素进行交换，将基准元素放置在正确的位置。
8. 对基准元素左边的子数组和右边的子数组进行递归排序，重复上述步骤。

## 代码

```go
// Some code
package main

import "fmt"

// 快速排序算法
func quickSort(arr []int, low, high int) {
	if low < high {
		// 选择一个基准元素
		pivot := partition(arr, low, high)

		// 对基准元素左边的子数组进行排序
		quickSort(arr, low, pivot-1)

		// 对基准元素右边的子数组进行排序
		quickSort(arr, pivot+1, high)
	}
}

// 划分函数，用于确定基准元素的位置
func partition(arr []int, low, high int) int {
	// 选择最右边的元素作为基准元素
	pivot := arr[high]

	// 将小于基准元素的元素交换到左边，大于基准元素的元素交换到右边
	i := low - 1
	for j := low; j <= high-1; j++ {
		if arr[j] < pivot {
			i++
			arr[i], arr[j] = arr[j], arr[i]
		}
	}
	arr[i+1], arr[high] = arr[high], arr[i+1]

	// 返回基准元素的位置
	return i + 1
}

func main() {
	arr := []int{64, 34, 25, 12, 22, 11, 90}
	quickSort(arr, 0, len(arr)-1)
	fmt.Println("排序结果:", arr)
}
```
