---
title: ECMAScript6之初识变量
date: 2017-05-28 09:54:17
categories:
  - ECMAScript6
tags: [javascript]
---

ECMAScript 6（以下简称ES6）是JavaScript语言的下一代标准。因为当前版本的ES6是在2015年发布的，所以又称ECMAScript 2015，也就是说，ES6就是ES2015。

虽然目前并不是所有浏览器都能兼容ES6全部特性，但越来越多的程序员在实际项目当中已经开始使用ES6了。所以就算你现在不打算使用ES6，但为了看懂别人的你也该懂点ES6的语法了...

#### ES6新增的let const命令

* let 适合在for循环中使用
* const 不能重新定义 不存在变量提升
如下：会打印 0 1 2 如果换成var 则打印 3 3 3

```
    const oLi = document.querySelectorAll('li');
       for(let i=0;i<oLi.length;i++){
        oLi[i].onclick = function(){
           console.log(i)
        }
       }

```
#### let const 重新重新声明同一个变量会报错

```
       let a = '1'
       let a = '32'
       console.log(a) //报错 提示已经有过声明 const一样

```

来个错误示范1
```
{
  var a =1;
  let a =2;  //报错，因为a已经用var声明过
}
```
来个错误示范2
```
{
  let a =1;
  let a= 2; //还是报错，a已经用let声明过。
}
```

#### const的特点不可修改
修改报错
```
const Name = '张三';
    Name = '李四';//错误，企图修改常量Name
    ```
与let类似只在块级作用域起作用
```
if(1){
       const Name = '张三';
     }
    alert(Name);//错误，在代码块{ }外，Name失效
```
不存在变量提升
```
if(1){
        alert(Name);//错误，使用前未声明
        const Name = '张三';
    }
 ```
 声明后必须要赋值
 ```
 const NAME; //错误，只声明不赋值
 ```
 const声明的对象可以修改 引用的一个新地址空间
 ```
  const Person = {"name":"张三"};
     Person.name = "李四";
     Person.age = 20;
     console.log(Person);//结果：正常输出{name: "李四", age: 20}

 ```