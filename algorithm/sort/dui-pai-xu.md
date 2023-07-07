# 堆排序

{% hint style="info" %}
**堆排序（Heap Sort）**：将数组构建为一个最大堆（或最小堆），然后逐步从堆中取出最大（或最小）的元素，并重新构建堆。
{% endhint %}

## 步骤

1. **构建最大堆**：将待排序的数组看作是一个完全二叉树，并按照从下到上、从右到左的顺序，对每个非叶子节点进行下沉操作，使得每个节点都大于其子节点。这样构建出的堆称为最大堆。
2. **交换堆顶和末尾元素**：将最大堆的堆顶元素（最大值）与数组末尾元素进行交换。
3. **调整堆**：将剩余的 n-1 个元素重新构建成最大堆，再次交换堆顶元素与当前末尾元素。
4. **重复步骤2和步骤3**，直到堆中的所有元素都被取出并放置在正确的位置。

## 代码

```go
// Some code
package main

import "fmt"

// 堆排序算法
func heapSort(arr []int) {
	// 构建最大堆
	n := len(arr)
	for i := n/2 - 1; i >= 0; i-- {
		heapify(arr, n, i)
	}

	// 依次取出堆顶元素，并调整堆
	for i := n - 1; i > 0; i-- {
		// 将堆顶元素与当前末尾元素交换
		arr[0], arr[i] = arr[i], arr[0]

		// 调整堆
		heapify(arr, i, 0)
	}
}

// 将以 root 为根节点的子树调整为最大堆
func heapify(arr []int, n, root int) {
	largest := root   // 假设根节点最大
	left := 2*root + 1
	right := 2*root + 2

	// 找到根节点、左子节点和右子节点中的最大值
	if left < n && arr[left] > arr[largest] {
		largest = left
	}
	if right < n && arr[right] > arr[largest] {
		largest = right
	}

	// 如果最大值不是根节点，则交换节点，并递归调整堆
	if largest != root {
		arr[root], arr[largest] = arr[largest], arr[root]
		heapify(arr, n, largest)
	}
}

func main() {
	arr := []int{64, 34, 25, 12, 22, 11, 90}
	heapSort(arr)
	fmt.Println("排序结果:", arr)
}
```
