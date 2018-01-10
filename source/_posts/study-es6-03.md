---
title: ECMAScript6之字符串的特性
date: 2017-05-29 17:54:17
categories:
  - ECMAScript6
tags: [javascript]
---

ES6对字符串新增了一些函数和操作规范，使得开发者对字符串的操作更加方便，以往需要借助其他javascript代码才能实现的效果，现在利用这些函数即可快速实现。

####  模板字符串
```
//传统的字符串拼接方式

let name = 'zhangsan'
let age = '30'
let str = 'he is ' + name +',' + 'age '+ age ;
console.log(str) //he is zhangsan,age 30

es6拼接
//用反引号 `${age}`包裹  把变量放入大括号中 有多少空格就会输出多少空格

let str2 = `he is ${name},age is ${age}`
console.log(str2) // he is zhangsan,age is 30


es6中可直接对字符串换行

let str3 = `write once ,
            write once`;
 console.log(str3) //write once ,
                                 //write once

```
#### ${}中可以放任意JavaScript表达式
```
//${ }运算
 var a = 1;
 var b = 2;
 var total = ` is ${a+b}`
 console.log(total) // is 3

  //${ }对象的属性
 var obj = {'as':11 , 'bs':22}
 var strs = ` is ${obj.as} and ${obj.bs}`
 console.log(strs) // is 11 and 22

  //${ } 函数的调用
  function fn(){
     return 3
  }
  var stra = `is ${ fn() }`
  console.log(stra) //is 3  结果是函数的返回值
```
#### 标签模板
标签模板简单的理解就是：“标签”指的就是函数，紧跟在后面的模板字符串就是它的参数。

```
alert`123`
// 等同于
alert(123)


//在函数中的运用 拼接的字符串就是函数的参数

var names = 'lxm';
var ages = '18';

tagFn`我${names},age${ages}`;
function tagFn(arr,v1,v2){ //第一个参数是数组
    console.log(arr) //["我", ",age", "", raw: Array(3)]
    console.log(v1) //lxm
    console.log(v2) //18
}

```
#### repeat()函数

```
//重复字符串，而不影响原有字符串 举个栗子
var strs = 'lxm';
var strs2 = strs.repeat(2);
console.log(strs2) //lxmlxm
```
#### includes()函数
```
//判断字符串中是否含有指定的子字符串，返回true表示含有和false表示未含有。
//第二个参数选填，表示开始搜索的位置。

var tit = '我是一个前端工程师';
var tits =  tit.includes('前');
var tits2 =  tit.includes('前',6);
console.log(tits) //true
console.log(tits2) //false 表示从第6个数开始找,没找到所以返回false
```
#### startsWith()函数
```
//判断指定的子字符串是否出现在目标字符串的开头位置，第二个参数选填，表示开始搜索的位置。

var titer = '前端开发工程师';
var titer1 = titer.startsWith('前');//true 前是在开头位置
var titer2 = titer.startsWith('端');//false
var titer3 = titer.startsWith('端', 1);//true 从第二个字符开始
console.log(titer1)
console.log(titer2)
console.log(titer3)

```
#### endsWith()函数
```
//判断子字符串是否出现在目标字符串的尾部位置，第二个参数选填，表示针对前N个字符。

var tname = '我是一枚美女';
console.log(tname.endsWith('女')) //true 是以女结尾的
console.log(tname.endsWith('我')) //false
console.log(tname.endsWith('我',2)) //前两个字符 是不是以我字结尾 返回false

```
#### codePointAt()函数 返回十进制数
```
//需要4个字符存储length为2的字节，对于4字节的字符，
//javascript无法正确读取字符，用charAt会出现乱码，
//使用ES6给我们提供的codePointAt( )函数可以处理4字节的字符串

var  stri2 = '𠮷';
console.log(stri2.charAt(0)) //乱码
console.log(stri2.codePointAt()) //134071十进制数 Unicode编码则是\u20bb7

//String.fromCodePoint()函数 返回正确的字符
//函数的参数是一个字符对应的码点，返回的结果就是对应的字符，哪怕这个字符是一个4字节的字符

console.log(String.fromCodePoint(134071)) //𠮷

```
#### String.raw``函数
不用括号用反引号即直接加模板字符串
```
//返回字符串最原始的样貌，如果有换行符\n也忽略会直接输出

console.log(`hello\nworld`);
console.log(String.raw`hello\nworld`); //hello\nworld

// 先转10进制 在输出字符对应的码点

var stt = '𠮷';
var stt2 = stt.codePointAt()
console.log(String.fromCodePoint(stt2)) //不会乱码 可正常输出 𠮷

```