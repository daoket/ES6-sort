## 归并排序 Merge Sort
### 原理：归并排序使用分而治之的思想，以折半的方式来递归/迭代排序元素，利用空间来换时间，做到了时间复杂度 O(n·log(n)) 的同时保持了稳定。

### 时间复杂度
- 最优时间复杂度： O(nlogn)
- 最坏时间复杂度： O(nlogn)
- 稳定性：稳定

实现方式
```
function merge_sort(arr) {
  let len = arr.length
  if (len <= 1) {
    return arr
  }
  let num = Math.floor(len / 2)
  let left = merge_sort(arr.slice(0, num))
  let right = merge_sort(arr.slice(num, arr.length))
  return merge(left, right)

  function merge(left, right) {
    let [l, r] = [0, 0]
    let result = []
    while (l < left.length && r < right.length) {
      if (left[l] < right[r]) {
        result.push(left[l])
        l++
      } else {
        result.push(right[r])
        r++
      }
    }
    result = result.concat(left.slice(l, left.length))
    result = result.concat(right.slice(r, right.length))
    return result
  }
}
let arr = [7, 4, 3, 67, 34, 1, 8]
let newArr = merge_sort(arr) // [ 1, 3, 4, 7, 8, 34, 67 ]
console.log(newArr)
```