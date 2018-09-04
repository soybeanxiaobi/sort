#### 一、 选择排序
1. 概念理解:
在一个长度为3的数组中，在第一趟遍历3个数据，找出其中<b>最小的数值与第一个元素交换</b>；  
第二趟遍历2个数据，找出其中<b>最小的元素与第一个数交换</b>(注意:这里的第一个数是指遍历的第一个数,实质上是数组的第二个数)  
而第三趟则是和自己比较,位置还是原来的位置

2. 复杂度: 
平均时间复杂度：O（n^2）

3. 例子:
```
//选择排序
function selectionSortFn(arr){
    console.log('原数组:['+ arr + ']')
    
    for (var i = 0; i < arr.length; i++) {
        for (var j = i+1; j < arr.length; j++) {
            if (arr[i] > arr[j]) {
                var temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }
        console.log(arr);
    }
    return arr;
}

var initArr = [10, 4, 8, 3];
selectionSortFn(initArr);
```
我们看一下打印的结果:
![选择排序]![](https://img2018.cnblogs.com/blog/1414709/201809/1414709-20180904192019606-870722484.png)  
```
原数组:[10,4,8,3]
[3, 10, 8, 4]
[3, 4, 10, 8]
[3, 4, 8, 10]
[3, 4, 8, 10]
```
结合概念就很好理解了。

#### 二、 冒泡排序
1. 概念理解:
    依次比较相邻的两个数，将小数放在前面，大数放在后面。  
第一趟：首先比较第一个和第二个数，将小数放前，大数放后，然后比较第二个数和第三个数将小数放前，大数放后，如此继续，直至比较最后两个数，将小数放前，大数放后,至此第一趟结束。  
在第二趟：仍从第一对数开始比较 （因为可能由于第2个数和第3个数的交换，使得第1个数不再小于第2个 数），将小数放前中，大数放后，一直比较到倒数第二个数（倒数第一的位置上已经是最大的），第二趟 结束。在倒数第二的位置上得到一个新的最大数（其实在整个数列中是第二大的数）。  
如此下去，重复以上过程，直至最终完成排序。
2. 复杂度
时间复杂度：O（n^2）

3. 例子
```
//冒泡排序
function bubbleSortFn(arr){
    console.log('原数组:['+arr + ']')
    
    for (var i = 0; i < arr.length-1; i++) {
        for (var j = 0; j < arr.length-1-i; j++) {
        //每次比较都会确定一个最小数，所以j < arr.length-1-i
            if (arr[j] > arr[j+1]) {
                var temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;
            }
        }
        console.log(arr)
    }
    return arr;
}

var initArr = [10, 4, 8, 3];
bubbleSortFn(initArr);
```
我们看一下打印的结果:    
![冒泡排序](https://img2018.cnblogs.com/blog/1414709/201809/1414709-20180904192723428-152367669.png)
```
原数组:[10,4,8,3]
[4, 8, 3, 10]
[4, 3, 8, 10]
[3, 4, 8, 10]
```
#### 三、 快速排序
1. 概念理解:
    * 在带排序的元素中任取一个元素作为基准（通常选第一个），称为基准元素；
    * b将带排序的元素进行分区，比基准元素大的元素放在他的右边，比他小的放在左边；
    * c对左右两个分区重复以上步骤(递归)直达所有元素有序；
2. 复杂度
时间复杂的：O（nlogn）
3. 例子
```
//快速排序
function quickSortFn(arr){
    console.log('原数组:['+arr + ']')
    // 如果数组长度<=1 ，则直接返回
    if (arr.length <= 1) return arr;
    //
    var bisectionIndex = Math.floor(arr.length/2);
    // 找基准，把基准从原数组中删除
    var bisection = arr.splice(bisection,1)[0];
    // console.log(bisection);

    // 定义作用数组
    var left = [];
    var right = [];

    // 比基准小的放left ，比基准大的放right
    for (var i = 0; i < arr.length; i++) {
        if (arr[i] <= bisection) {
            left.push(arr[i]);
        }else{
            right.push(arr[i]);
        }
        console.log(arr);
    }
    //递归
    return quickSortFn(left).concat([bisection],quickSortFn(right));
}

var initArr = [10, 4, 8, 3];
quickSortFn(initArr);
```
我们看一下打印结果:
![](https://img2018.cnblogs.com/blog/1414709/201809/1414709-20180904195757688-276030582.png)  
```
[4, 8, 3]
[4, 8, 3]
[4, 8, 3]
[8, 3]
[8, 3]
```
#### 四、插入排序
1. 概念理解:
检查第i个数字，如果在它的左边的数字比它大，进行交换，这个动作一直继续下去，直到这个数字的左边数字比它还要小，就可以停止了。

2. 复杂度
时间复杂度：O（n^2）

3. 例子
```
//插入排序
function insertSortFn(arr){
    console.log('原数组:['+arr + ']')
    for (var i = 1; i < arr.length; i++) {
        var temp = arr[i];
        for (var j = i-1; j >=0 && temp < arr[j]; j--) {
            arr[j+1] = arr[j];
            arr[j] = temp;
        }
        console.log(arr)
    }
    return arr;
}

var initArr = [10, 4, 8, 3];
insertSortFn(initArr);
``` 
我们看一下打印结果:
![插入排序](https://img2018.cnblogs.com/blog/1414709/201809/1414709-20180904195209317-8289999.png)

```
原数组:[10,4,8,3]
[4, 10, 8, 3]
[4, 8, 10, 3]
[3, 4, 8, 10]
```

#### 四、总结
1. 冒泡排序是排序里面最简单的了，但性能也最差，数量小的时候还可以，数量多，是非常慢的。
2. 冒泡、选择、插入三个排序复杂度都是一样的(慢)
2. 快速排序效率最高。平均时间复杂度是 O(Nlog2N)，最差也是O(N*N)，空间复杂度O(Nlog2N) 
