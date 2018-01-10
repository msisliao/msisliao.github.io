---
title: ECMAScript6之字数值的特性
date: 2017-05-30 12:54:17
categories:
  - ECMAScript6
tags: [javascript]
---

来看看es6对数值做了哪些扩展

```
    /*-----在ES6的标准中,数值属性都移植到了Number下 使用时Number.isNan Number.parseFloat...*/
    console.log(isNaN('abc')) //true  'abc'无法转为一个数值，返回true
    console.log(Number.isNaN(1.1)) //flase 因为2.5是一个数值
    console.log(Number.isNaN('abc')) //false  'abc'是字符串，Number.isNaN不做类型转换，直接返回false

```
#### 新增Number.isInteger函数
```
//用来判断是否是整数。

console.log(Number.isInteger(41.1)) //false
console.log(Number.isInteger(3)) //true
console.log(Number.isInteger(3.01)) //false

```

<!--more-->

#### isSafeInteger判断整数是否安全
```
    //返回Boolean值 可以正常显示的整数范围在-2^53到2^53之间 超出为不安全

  console.log(Number.isSafeInteger(Number.MAX_SAFE_INTEGER)) //true
  console.log(Number.isSafeInteger(Number.MAX_SAFE_INTEGER+1)) //false
  console.log(Number.MAX_SAFE_INTEGER) //是最大安全整数

```
#### Math.trunc函数
```
    //用于去除小数部分，返回整数

    console.log(Math.trunc(3)) //3
    console.log(Math.trunc(3.4)) //3

```
#### Math.sign函数
```
    //用于判断一个数到底是正数、负数、还是零。
    //整数---- 1  负数---- -1  0--- 0 非数值-- NaN

    console.log(Math.sign(2.5)) //1
    console.log(Math.sign(-0.9)) //-1
    console.log(Math.sign(0)) //0
    console.log(Math.sign('abv')) //NaN


```
####  Math.cbrt函数
```
    //用于计算一个数的立方根

    console.log(Math.cbrt(8))//2  2的三次方是8
    console.log(Math.cbrt(27))//3  2的三次方是8

```
#### es6中新增的一些数学方法
```
    Math.acosh(x) //返回 x 的反双曲余弦。
    Math.asinh(x) //返回 x 的反双曲正弦。
    Math.atanh(x) //返回 x 的反双曲正切。
    Math.clz32(x) //返回 x 的 32 位二进制整数表示形式的前导 0 的个数。
    Math.sinh(x) //返回x的双曲正弦。
    Math.cosh(x) //返回 x 的双曲余弦。
    Math.expm1(x) //返回 eˆx - 1。
    Math.fround(x) //返回 x 的单精度浮点数形式。
    Math.hypot(...values) //返回所有参数的平方和的平方根。
    Math.imul(x, y) //返回两个参数以 32 位整数形式相乘的结果。
    Math.log1p(x) //返回 1 + x 的自然对数。
    Math.log10(x) //返回以 10 为底的x的对数。
    Math.log2(x) //返回以 2 为底的 x 的对数。
    Math.tanh(x) //返回 x 的双曲正切。
```
好多数学方法~~用到时查资料吧！！