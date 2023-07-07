# 💖 动态规划

**动态规划（Dynamic Programming）**：是一种解决复杂问题的算法思想，通过将问题拆解为更小的子问题，并利用子问题的解来求解原始问题。它通常用于解决具有重叠子问题和最优子结构性质的问题。

## 步骤

1. **确定状态**: 将原问题划分为子问题，并定义子问题的状态。状态是描述问题的一个或多个变量的值。
2. **定义状态转移方程**: 根据子问题和原问题之间的关系，建立状态转移方程。状态转移方程描述了问题从一个状态转移到另一个状态的方式。
3. **确定初始条件**: 确定最简单的子问题的解，即初始条件。这些初始条件将作为动态规划算法的起点。
4. **计算顺序**: 根据状态转移方程，按照一定的计算顺序，计算子问题的解，并逐步推导出原问题的解。
5. **解决原问题**: 最终得到原问题的解，它通常对应于最终的状态。

## 代码

```go
// Some code
package main

import "fmt"

// 动态规划解决背包问题
func knapsack(weights []int, values []int, capacity int) int {
	n := len(weights)
	// 创建二维数组来存储子问题的解
	dp := make([][]int, n+1)
	for i := range dp {
		dp[i] = make([]int, capacity+1)
	}

	// 填充数组，计算每个子问题的最优解
	for i := 1; i <= n; i++ {
		for j := 1; j <= capacity; j++ {
			if weights[i-1] <= j {
				// 当前物品可以装入背包
				dp[i][j] = max(values[i-1]+dp[i-1][j-weights[i-1]], dp[i-1][j])
			} else {
				// 当前物品无法装入背包
				dp[i][j] = dp[i-1][j]
			}
		}
	}

	// 返回原问题的解
	return dp[n][capacity]
}

// 辅助函数，返回两个整数的较大值
func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}

func main() {
	weights := []int{2, 3, 4, 5}   // 物品的重量
	values := []int{3, 4, 5, 6}    // 物品的价值
	capacity := 8                  // 背包的容量
	maxValue := knapsack(weights, values, capacity)
	fmt.Println("背包问题的最大价值:", maxValue)
}
```
