---
title: js中的===和==和Object.is
date: 2019-01-08 21:05:29
tags: 随笔
---

今天在项目中遇到一个有趣的现象,使用===判断0和-0时会返回true,趁此机会回顾一下js中判断变量是否相等的方法;
<!-- more -->
### 1:===方法和==方法
这两个方法用的最多,===会连自动转换变量的类型进行判断比如```console.log('1'===1)```===会返回false而==会返回true,==对了一步隐藏的转换类似
``` parseFloat('1')===1```
---
但是===会有异常现象
* 0===-0会返回true
* NaN===NaN 会返回false(NaN和任何值比较会返回false)

### 2:ES6新增的方法 Object.is
Object.is 是ES6新增的严格判断两个值是否相等的方法,用法
```
console.log('1',1); //false
console.log(1,1) //false
console.log(0,-0) //false
console.log(NaN,NaN) //true
```
可以看到Object.is 在=== 的基础上添加了对0和-0,和NaN 的判断逻辑,在代码中尽量使用Object.is,兼容性问题可以使用shim等工具
### 3:手动实现Object.is
```
if(!Object.is){
    Object.is=function(a,b){
        if(a===0&&b===0){
            return 1/a===1/b
        }
        if(a!==a){
            return b!==b;
        }
        return a===b;
    }
}

```

