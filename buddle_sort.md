# 冒泡排序 Bubble Sort
### 原理：依次比较、交换相邻的元素大小
### 时间复杂度
- 最优时间复杂度：O(n^2)
- 最坏时间复杂度：O(n)
- 稳定性：稳定


实现方式1
```
function buddle_sort(arr) {
  let len = arr.length - 1
  for (let j = 0; j < len; j++) {
    for (let i = 0; i < len - j; i++) {
      if (arr[i] > arr[i + 1]) {
        [arr[i], arr[i + 1]] = [arr[i + 1], arr[i]]
      }
    }
  }
}

let arr = [7, 4, 3, 67, 34, 1, 8]
buddle_sort(arr)
console.log(arr)  // [ 1, 3, 4, 7, 8, 34, 67 ]
```
解析： 依次比较相邻两个数大小，每次内循环都会将内循环中最大的数移到最后，内循环长度-1
循环参数： 外循环： 0-->n-1, 内循环：0-->n-1-j
```
 j:0  i: 0-6 --> [ 4, 3, 7, 34, 1, 8, 67 ]  将0-6中最大的移到最后
 j:1  i: 0-5 --> [ 3, 4, 7, 1, 8, 34, 67 ]  将0-5中最大的移到最后
 ...
 j:6  i: 0-0 --> [ 1, 3, 4, 7, 8, 34, 67 ]  将0-0中最大的移到最后
```

实现方式2
```
function buddle_sort(arr, fn) {
  let len = arr.length
  let count = 0
  while (len--) {
    for (let i = 0; i < len; i++) {
      if (arr[i] > arr[i + 1]) {
        [arr[i], arr[i + 1]] = [arr[i + 1], arr[i]]
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
buddle_sort(arr1)  // [ 1, 3, 4, 7, 8, 34, 67 ]   时间复杂度：O(n^2) 
buddle_sort(arr2)  // [ 1, 3, 4, 7, 8, 34, 67 ]   时间复杂度：O(n)
```
解析： 想象一下，如果我们输入的本来就是一个有序序列，其实只需要一次循环就够了，所以我们需要针对特殊情况进行优化
### 蚂蚁金服面试
对于冒泡排序来说，能不能传入第二个参数（参数为函数），来控制升序和降序？
```
function buddle_sort(arr, fn) {
  let len = arr.length
  while (len--) {
    for (let i = 0; i < len; i++) {
      if (fn(arr[i], arr[i + 1]) > 0) {
        [arr[i], arr[i + 1]] = [arr[i + 1], arr[i]]
      }
    }
  }
}

let arr = [7, 4, 3, 67, 34, 1, 8]
buddle_sort(arr, (a, b) => a - b) // [ 1, 3, 4, 7, 8, 34, 67 ]
buddle_sort(arr, (a, b) => b - a) // [ 67, 34, 8, 7, 4, 3, 1 ]

```