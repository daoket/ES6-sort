# 快速排序 Quick sort
### 原理：
- 从数列中挑出一个元素，称为"基准"（pivot）
- 重新排序数列，所有比基准值小的元素摆放在基准前面，所有比基准值大的元素摆在基准后面（相同的数可以到任何一边）。在这个分区结束之后，该基准就处于数列的中间位置。这个称为分区（partition）操作。
- 递归地（recursively）把小于基准值元素的子数列和大于基准值元素的子数列排序。

### 时间复杂度
- 最优时间复杂度： O(nlogn) 
- 最坏时间复杂度： O(n^2) 
- 稳定性：不稳定

实现方式
```
function quick_sort(arr, start, end) {
  if (start >= end) {
    return
  }

  let mid = arr[start]
  let low = start
  let high = end

  while (low < high && arr[high] >= mid) {
    high--
  }
  arr[low] = arr[high]

  while (low < high && arr[low] < mid) {
    low++
  }
  arr[high] = arr[low]

  arr[low] = mid
  quick_sort(arr, start, low - 1)
  quick_sort(arr, low + 1, end)
}

let arr = [7, 4, 3, 67, 34, 1, 8]
quick_sort(arr, 0, arr.length - 1)
console.log(arr) // [ 1, 3, 4, 7, 8, 34, 67 ]
```
分析： 第一次外层while循环跳出，将数组分成左边两部分，中间为7， 左边都比7小，右边都比7大，之后将左边数组传入递归，当左边全部排好后，才会将右边数组传入进行递归，循环结束后，如果我们以7为根节点，可以转化一个典型的二叉树，而我们上面的操作像不像深度优先遍历的递归算法。
