---
title: JavaBase_07:循环结构
date: 2021-05-03 20:16:22
tags: [Java,学习笔记]
categories: 
  - Study Notes
  - Java
mermaid: true
---
看各种视频教程出来的大杂烩笔记，对他人作用估计不大。内容：循环结构
<!-- more -->

# while循环

- 判断是否满足条件，为true则进入循环执行语句，为false则跳出循环
- 条件判断为true时，循环会一直执行

```java
while(条件判断){
    //循环内容
}
```
# do...while循环

- 先执行一次语句，再做循环条件判断

```JAVA
do {
    //代码语句
}while(条件判断);
```

- while是先判断后执行，do...while 是先执行后判断

# for循环

- 当满足条件的时候，会执行重复执行的循环体 ，如果一旦判断不满足,就结束循环。 

```JAVA
  for(条件初始化;条件判断;条件迭代){
			重复执行的语句;
		}
```        

- 死循环

```JAVA
//
  for( ; ; ){
			重复执行的语句;
		}
```
- 可以迭代数组和集合，取出其中的元素。
  - 只适合取数据，不能更改数据
  - 只用于数组，或实现Iterable接口的集合类上；set，list

```JAVA
//
for(声明语句 : 表达式)
{
   //代码句子
}


public static void main(String[] args){
    int arr[] = {1,2,3};
    /**
    *增强for
    */
    for(int num : arr){
     System.out.println(num);
     }
}

```

# break 关键字
- break 主要用在循环语句或者 switch 语句中，用来中止循环,跳出整个语句块。

```java
public static void main(String[] args) {

        int [] numbers = {10, 20, 30, 40, 50};

        for(int x : numbers ) {
            if( x == 30 ) {
                break;
            }
            System.out.println( x );
        }
    }  
```    
> 输出结果
>10
>20

# continue 关键字
- continue 适用于任何循环控制结构中。作用是让程序立刻跳出本次循环，跳到下一次循环的迭代,并不是中止循环。
  - 在 for 循环中，continue 语句使程序立即跳转到更新语句。
  - 在 while 或者 do…while 循环中，程序立即跳转到布尔表达式的判断语句。

```java
public static void main(String[] args) {

        int [] numbers = {10, 20, 30, 40, 50};

        for(int x : numbers ) {
            if( x == 30 ) {
                continue;
            }
            System.out.println( x );
        }
    }  
```    
> 输出结果
>10
>20
>40
>50
