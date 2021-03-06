## 背景

查找问题是计算机中非常重要的基础问题

## 二分查找法(Binary search)

对于有序数列，才能使用二分查找法(排序的作用)

[二分查找法](http://linyimin-blog.oss-cn-beijing.aliyuncs.com/cjoeekbg30000wqkhbhqge38z.png)

查找步骤：

1. 数组中间元素与目标元素V比较，如果两个元素相等，则直接返回，否则进行第二步：
2. 数组分为大于V和小于V的两部分， 如果中间元素大于目标元素V，则在大于V的部分重复第一步，否则在小于V的部分重复第一步。直至找目标元素。

**代码实现**

```ts
function binarySearch (arr: number[], target: number): number {
    let l = 0
    let r = arr.length - 1
    while (l < r) {
      let mid = l + Math.floor((r - l) / 2)
      if (target === arr[mid]) {
        return mid
      }

      if (target > arr[mid]) {
        l = mid + 1
      } else {
        r = mid - 1
      }
    }
    return -1
  }
```

**递归代码实现**

```ts
 function binarySearchImplementWithRecursive (arr: number[], target: number): number {
    return __compare(arr, 0, arr.length - 1, target)
  }

  function __compare (arr: number[], l: number, r: number, target:number): number {
    if (l > r) {
      return -1
    }
    let mid = l + Math.floor((r - l)/2)
    if (target === arr[mid]) {
      return mid
    }
    if (target > arr[mid]) {
      return __compare(arr, mid+1, r, target)
    }

    return __compare(arr, l, mid-1, target)
  }
```

## 二分查找的变种

- floor函数

目标元素在数组中第一次出现的位置
- ceil函数

目标元素在数组中最后一次出现的位置

当目标元素不存在时：[](http://linyimin-blog.oss-cn-beijing.aliyuncs.com/cjoeggf9j0001wqkh2rrod5na.png)
