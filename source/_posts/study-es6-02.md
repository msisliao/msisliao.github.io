---
title: ECMAScript6之解构赋值
date: 2017-05-28 15:54:17
categories:
  - ECMAScript6
tags: [javascript]
---

什么是解构赋值？
> 官方的解释：ES6允许按照一定模式，从数组和对象中提取值，对变量进行赋值，这被称为解构（Destructuring）。

下面用代码来解释到底什么是解构赋值？
#### 关于给变量赋值，传统的是酱样子
```
    var arr = [1, 2, 3];
    var a = arr[0]
    var b = arr[1]
    var c = arr[2]
    console.log(a) //1
    console.log(b) //2
    console.log(c) //3

```
#### ES6如何给变量赋值呢（变量的解构赋值）
不需要分别把变量a，b，c分别声明定义和赋值，只需要将变量a，b，c作为一个数组的元素，然后将数组[1,2,3]赋值给数组[a,b,c]即可，变量a，b，c即可分别得到对应的值。
```
    var [aa, ba, ca] = [11, 21, 31]
    console.log(aa) //11
    console.log(ba) //21
    console.log(ca) //31

```
#### 解构赋值的嵌套
```
    var [a1, b1, [c1, c2, c3 = 1]] = [111, 222, [333, 334, 335]]
    console.log(c1) //333
    console.log(c3) //335 c3默认值为1  右侧重新赋值为335

```
#### 对象的解构赋值
```
    var {as, bs, cs} = {'as' : 12, 'bs' : 22, 'cs' : 32}
    console.log(as) //12

    var {as, bs, cs} = {'bs' : 22, 'cs' : 32, 'as' : 12,} //赋值的位置可随意 执行时属性名与属性值会对应
    console.log(cs) //32

```
#### 字符串的解构赋值
```
    var [a, b, c, d, e, f] = '我是zhangsan'
    console.log(a) //我
    console.log(b) //是
    console.log(c) //z

```
#### 解构赋值的用途
* 交换变量的值
```
 传统的方法
     var x = 1;
     var y = 2;
     var z = x;//第三个变量临时存放x的值
     x = y;  //把y的值赋给x；
     y = z;  //把z的值赋值给y；
     console.log(x); //结果：x为2
     console.log(y); //结果：y为1
es6的方法
    var x = 1;
    var y = 2;
    [x, y] = [y, x]                    // 简单的一句代码即可成功交换x，y的值
    console.log(x) //2
    console.log(y) //1

```
#### 提取函数返回的多个值
一般来说函数只能返回一个值，我们可以将多个值装在一个数组或者对象中，再用解构赋值快速提取其中的
```
    function demo(){
        return {'age' : 20, 'name' : 'lxm'}
    }
    var {age, name} = demo()             //实现快速提取函数返回的对应值
    console.log(age, name)


```
定义函数参数
```
    function demo2({a, b, c}){
        console.log('姓名:' + a)
        console.log('age:' + b)
        console.log('sex:' + c)
    }
    demo2({a : 'lxm', c : '12'});           //只需给想要的变量赋值而不用担心其它变量 b

```
#### 函数参数的默认值
传统的需要判断值为undefined然后给默认值
```
    function demo3(as){
        var name;
        if(as === undefined){
            name = '张三'
        } else {
            name = as
        }
        console.log('姓名' + name)
    }
    demo3()//姓名张三

```
ES6的解构赋值
```
    function demo4({name = 'zhangsan'}){
        console.log('姓名' + name)
    }
    demo4({}) //姓名zhangsan

```