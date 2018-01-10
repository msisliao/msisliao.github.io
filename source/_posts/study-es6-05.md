---
title: ECMAScript6之字数组的新特性
date: 2017-05-31 12:54:17
categories:
  - ECMAScript6
tags: [javascript]
---

#### Array.of()

```
//将一组数值转换为数组

   console.log(Array.of(1,3,4,'a')) //[1, 3, 4, "a"]
```
#### Array.from()


```
// 可以将类似数组的对象或者可遍历的对象转换成真正的数组。

    var OLi = document.querySelectorAll('li')
    console.log(typeof OLi) //对象
    console.log(Array.from(OLi)) //返回数组[li, li]

    var str = 'hello';
    console.log(Array.from(str)) //将字符串转成数组 [0:"h", 1:"e", 2:"l", 3:"l", 4:"o"]
```
#### find( )函数
```
// 找出数组中符合条件的第一个元素。
    var arrn = [1,2,3,4,56,7]
    var sn = arrn.find(function(value){
        return value > 7
    })
    console.log(sn) //56

```
#### findIndex( )函数
```
// 返回符合条件的第一个数组成员的位置。
    let arrnum = [2,8,9,100,89]
    let arrsn = arrnum.findIndex(function(value){
        return value > 10
    })
    console.log(arrsn) //3 返回符合结果的第一个索引  如果所有的都不符合则返回-1
```
#### fill()函数
```
// 用指定的值天填充到数组
    let arr1 = [1,2,5,8]
    //arr1.fill(3) 数组中的所有元素被填充4
    arr1.fill(3,1,2)
    console.log(arr1) //第一个是要填充的数 第二个是开始填充的位置 第三个是结束的位置(不包括结束) 其余数组的不变
```
#### entries()函数
```
// 对数组的键值对进行遍历，返回一个遍历器，可以用for..of对其进行遍历。
    for(let[i,v] of['a','b'].entries()){
        console.log(i,v) //[0:'a',1:'b']
    }
```
#### keys()函数
```
// 对数组的索引键进行遍历，返回一个遍历器。
   for(let index of['c','d'].keys()){
       console.log(index) // 0 1
   }

```
#### values()函数
```
// 对数组的元素进行遍历，返回一个遍历器 (火狐支持)
   for(let value of ['c','d'].values()){
       console.log(value) // c d
   }

```
#### 数组推导
```
// 用简洁的写法，直接通过现有的数组生成新数组
    //举例子 一个数组a 另一个数组在a数组的每个元素上乘以2
    var arra1 = [1,3,4,5,6]
    var arra2 = []
    for(var i=0;i<arra1.length;i++){
        arra2.push(arra1[i]*2)
    }
    console.log(arra2) //2 6 8 10 12

    //用es6数组维导的方法
    var arrb1 = [2,3,6]
    var arrb2 = [for(f of arrb1) f*2]
    console.log(arrb2) //4 6 12

    //可以加if条件
     var arrb3 = [for(j of arrb1) if(j>2) j] //数组的元素要大于2
     console.log(arrb3) //3 6


```