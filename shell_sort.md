# 希尔排序 Shell Sort
### 原理：插入排序的改进版，克服了插入排序每次只能移动相邻位置的缺陷，希尔排序每次可以移动gap个位置

### 时间复杂度
- 最优时间复杂度： O(nlogn) 
- 最坏时间复杂度： O(n^2) 
- 稳定性：不稳定

实现方式

```
function shell_sort(arr) {
  let len = arr.length
  let gap = Math.floor(len / 2)
  while (gap > 0) {
    for (let i = gap; i < len; i++) {
      let j = i
      while (j >= gap && arr[j - gap] > arr[j]) {
         [arr[j - gap], arr[j]] = [arr[j], arr[j - gap]]
         j -= gap
      }
    }
    gap = Math.floor(gap / 2)
  }
}
let arr = [7, 4, 3, 67, 34, 1, 8]
shell_sort(arr) // [ 1, 3, 4, 7, 8, 34, 67 ]
```