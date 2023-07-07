# 归并排序

{% hint style="info" %}
**归并排序（Merge Sort）**：将数组不断地分成两半，递归地对每个子数组进行排序，然后将排好序的子数组合并起来。
{% endhint %}

## 步骤

1. **拆分**：将待排序的数组递归地拆分成两个子数组，直到每个子数组只包含一个元素为止。
2. **合并**：将两个有序子数组合并为一个有序数组。创建一个额外的辅助数组，比较两个子数组的首个元素，将较小（或较大）的元素放入辅助数组中，并将对应子数组的指针向后移动一位。
3. **递归排序**：对两个拆分后的子数组分别进行递归排序，即重复步骤1和步骤2，直到子数组只包含一个元素。
4. **合并结果**：将两个有序的子数组合并为一个有序数组。将已排序的子数组合并时，需要比较子数组的元素，并将较小（或较大）的元素放入结果数组中。
5. **返回结果**：最后合并完成后，返回完全排序的数组。

## 代码

```go
// Some code
package main

import "fmt"

// 归并排序算法
func mergeSort(arr []int) []int {
	if len(arr) <= 1 {
		return arr
	}

	// 将数组拆分为两个子数组
	mid := len(arr) / 2
	left := mergeSort(arr[:mid])
	right := mergeSort(arr[mid:])

	// 合并两个子数组
	return merge(left, right)
}

// 合并两个有序数组
func merge(left, right []int) []int {
	result := make([]int, 0, len(left)+len(right))
	i, j := 0, 0

	// 比较两个子数组的元素，并按顺序合并到结果数组
	for i < len(left) && j < len(right) {
		if left[i] <= right[j] {
			result = append(result, left[i])
			i++
		} else {
			result = append(result, right[j])
			j++
		}
	}

	// 将剩余的元素追加到结果数组
	result = append(result, left[i:]...)
	result = append(result, right[j:]...)

	return result
}

func main() {
	arr := []int{64, 34, 25, 12, 22, 11, 90}
	sortedArr := mergeSort(arr)
	fmt.Println("排序结果:", sortedArr)
}
```
