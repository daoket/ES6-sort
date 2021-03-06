# 插入排序 Insertion Sort
### 原理：默认 a[0] 为已排序数组中的元素，从 arr[1] 开始逐渐往已排序数组中插入元素，从后往前一个个比较，如果待插入元素小于已排序元素，则已排序元素往后移动一位，直到待插入元素找到合适的位置并插入已排序数组。经过 n - 1 次这样的循环插入后排序完毕。

### 时间复杂度
- 最优时间复杂度： O(n) 
- 最坏时间复杂度： O(n^2) 
- 稳定性：稳定

实现方式1
```
function insert_sort(arr) {
  for (let j = 1; j < arr.length; j++) {
    for (let i = j; i > 0; i--) {
      if (arr[i] < arr[i - 1]) {
        [arr[i], arr[i - 1]] = [arr[i - 1], arr[i]]
      }
    }
  }
}
let arr = [7, 4, 3, 67, 34, 1, 8]
insert_sort(arr) // [ 1, 3, 4, 7, 8, 34, 67 ]
```
 实现思想： 将右边数组第一个截取，依次和左边已经排好序的值比较插入，插入位置不固定
 循环参数： 外循环： 0-->n-1, 内循环：j-->0  
```
j: 1 --> 6  i: j--> 0

j: 1  i: 1-->0  arr[1] < arr[0]=true  ---> [4, 7, 3, 67, 34, 1, 8]
j: 2  i: 2-->0  arr[2] < arr[1]=true  ---> [4, 3, 7, 67, 34, 1, 8]  --> [3, 4, 7, 67, 34, 1, 8]
... 
j: 6  i: 6-->0  arr[6] < arr[5]=true  --->  [ 1, 3, 4, 7, 34, 8, 67 ]  ---> [ 1, 3, 4, 7, 8, 34, 67 ]
```

实现方式2
```
function insert_sort(arr) {
  let count = 0
  for (let j = arr.length; j > 0; j--) {
    for (let i = j; i > 0; i--) {
      if (arr[i] < arr[i - 1]) {
        [arr[i], arr[i - 1]] = [arr[i - 1], arr[i]]
        count++
      }
    }
    if (count == 0) {
      return
    }
  }
}
let arr1 = [7, 4, 3, 67, 34, 1, 8]
let arr2 = [ 1, 3, 4, 7, 8, 34, 67 ]
insert_sort(arr1) // [ 1, 3, 4, 7, 8, 34, 67 ]   时间复杂度：O(n^2) 
insert_sort(arr2) // [ 1, 3, 4, 7, 8, 34, 67 ]   时间复杂度：O(n)
```