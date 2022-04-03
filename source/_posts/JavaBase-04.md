---
title: JavaBase_04:运算符
date: 2021-05-02 21:06:12
tags: [Java,学习笔记]
categories: 
  - Study Notes
  - Java
---
看各种视频教程出来的大杂烩笔记，对他人作用估计不大。内容：运算符
<!-- more -->

# 运算符

- 算术运算符：`+`,`-`,`*`,`/`,`%`,`++`,`--`
- 赋值运算符:`=`
- 关系运算符:`>`,`<`,`>=`,`<=`,`==`,`!=`,`instanceof`
- 逻辑运算符:`&&`,`||`,`!`
- 位运算符:`&`,`|`,`^`,`~`,`>>`,`<<`,`>>>`
- 条件运算符:`?:`
- 扩展赋值运算符:`+=`,`-=`,`*=`,`/=`



|优先级|运算符|简介|结合性|
|-|-|-|-|
|1|[ ]、 .、 ( ) |方法调用，属性获取|从左向右|
|2|!、~、 ++、 --|一元运算符|从右向左|
|3|* 、/ 、%|乘、除、取模（余数）|从左向右|
|4|+ 、 -|加减法|从左向右|
|5|<<、 >>、 >>>|左位移、右位移、无符号右移|从左向右|
|6|< 、<= 、>、 >=、 instanceof|小于、小于等于、大于、大于等于，对象类型判断是否属于同类型|从左向右|
|7|== 、!=|2个值是否相等，2个值是否不等于。下面有详细的解释|从左向右|
|8|&|按位与|从左向右|
|9|^|按位异或|从左向右|
|10|\||按位或|从左向右|
|11|&&|短路与|从左向右|
|12|\|\||短路或|从左向右|
|13|?:|条件运算符|从右向左|
|14|=、 += 、-= 、*= 、/=、 %=、 &=、 \|=、 ^=、 <、<= 、>、>= 、>>=|混合赋值运算符|从右向左|

## 算术运算符
**基础运算符`+`,`-`,`*`,`/`,`%`,**
```java
int a = 10;
int b = 20;
int c = 30;
int d = 40;
int e = 45;
System.out.println(a+b);            //加法运算，输出为30
System.out.println(a-b);            //减法运算，输出为-10
System.out.println(a*b);            //乘法运算，输出为200
System.out.println(a/b);            //除法运算，输出为0（int型直接舍弃小数）
System.out.println(a/(double)b);    //除法运算，强转为double型再进行计算，输出为0.5
System.out.println(e%d);            //模（取余）运算，计算出无法整除的数，输出为5
```    

**自增`++`,自减`--`**
```java
int a = 1;
//定义int型变量a，赋值为1
System.out.println(a);
//输出为a的值1
System.out.println(a++);
//先执行语句，将a的值'1'输出；再将a进行自增，a的值自增后为'2'
System.out.println(a);
//输出a此时的值'2'
System.out.println(++a);
//先将a进行自增，得出值为3；再执行语句，将a的值输出，输出值为'3'
System.out.println(a);
//输出a此时的值'3'
System.out.println(a--);
//先执行语句，将a的值'3'输出；再将a进行自减，a的值自增后为'2'
System.out.println(a);
//输出a此时的值'2'
System.out.println(--a);
//先将a进行自增，得出值为1；再执行语句，将a的值输出，输出值为'1'
System.out.println(a);
//输出a此时的值'1'
```    
## 赋值运算符
```java
int a = 1;
int b = 2;
System.out.println(a);//输出结果为1;
System.out.println(b);//输出为2;
b = a;//将a的值赋给b
System.out.println(b);//输出为1
```    

## 关系运算符
**`>`,`<`,`>=`,`<=`,`==`,`!=`**
- 用于用来比较判断两个变量或常量的大小
- 关系运算符是二元运算符，运算结果是 boolean 型。当运算符对应的关系成立时，运算结果是 true，否则是 false
- 基本类型的变量、值不能和引用类型的变量、值进行比较
- 如果两个引用类型之间没有父子继承关系，那么它们的变量不能使用 == 进行比较
- 两个引用类型有父子继承关系只可以 == 比较 ；不能进行 >,<,>=,<=比较
- boolean 类型的变量、值不能与其他任意类型的变量、值进行比较
- 关系运算符的优先级为：>、<、>=、<= 具有相同的优先级，并且高于具有相同优先级的 !=、==

> **`>`,`<`,`>=`,`<=`只支持左右两边操作数是数值类型**
```java
int a = 1;
int b = 2;
System.out.println(a>b);//条件不成立,返回false
System.out.println(a>=b);//条件不成立,返回false
System.out.println(a<b);//条件成立,返回true
System.out.println(a<=b);//条件成立,返回true
System.out.println(a==b);//条件不成立,返回false
System.out.println(a!=b);//条件成立,返回true
```
> `int型`和`char型`进行比较
```java
char a = 'a';//(int)a为97
char b = '2';//(int)b为50
int c = 50;

System.out.println(a>b);//true
System.out.println(a<b);//false
System.out.println(a==b);//false

System.out.println(a>c);//true
System.out.println(a<c);//false
System.out.println(a==c);//false
        
System.out.println(c>b);//false
System.out.println(c<b);//false
System.out.println(c==b);//true
```
## 逻辑运算符
- 与`&&`：两个值都为真，则结果为true
- 或`||`：两个值有一个值为true，则结果为true
- 非`!`：将值取反，如果是true则为false，如果是false则为true
```java
    // 与(and)  或(or) 非(取反)
boolean a = true;
boolean b = false;

System.out.println("a && b"+(a && b));  //false
System.out.println("a || b:"+(a||b));   //true
System.out.println("!(a && b):"+!(a&&b));  //true
```

```java
//短路运算
int c = 5;
boolean d = (c<4)&&(c++<4);  //因为c<4为false，直接输出false，不执行c++
System.out.println(d);  //false
System.out.println(c);  // 5


int c = 5;
boolean d = (c>4)&&(c++<4);  //因为c>4为true，需要判断c++<4，执行c++
System.out.println(d);  //c++<4为false,true&&false,输出为false
System.out.println(c);  // 6



int c = 5;
boolean d = (c>4)||(c++<4);  //因为c>4为true，直接输出true，不执行c++
System.out.println(d);  //true
System.out.println(c);  // 5



int c = 5;
boolean d = (c<4)||(c++>4);  //因为c<4为false，需要判断c++>4，执行c++
System.out.println(d);  //c++>4为true,false||true,输出为true
System.out.println(c);  // 6
```

## 位运算符
`&`按位与操作，按二进制位进行"与"运算。运算规则：（有 0 则为 0，两个位都为1时，结果才为1）
```java
0&0=0;   
0&1=0;    
1&0=0;     
1&1=1;
```
`|`按位或运算符，按二进制位进行"或"运算。运算规则：（有 1 则为 1）
```java
0|0=0;   
0|1=1;   
1|0=1;    
1|1=1;
```

`^`异或运算符，按二进制位进行"异或"运算。
```java
0^0=0;   
0^1=1;   
1^0=1;  
1^1=0;
```


`~`取反运算符，按二进制位进行"取反"运算
```java
~1=-2;   
~0=1;
```
`<<`二进制左移运算符。将一个运算对象的各二进制位全部左移若干位（左边的二进制位丢弃，右边补0）

```java
//<< 左移
//<<  *2
System.out.println(2<<3);  // 输出为16

```
`>>`二进制右移运算符。将一个数的各二进制位全部右移若干位，正数左补0，负数左补1，右边丢弃

```java
//>> 右移
//>>  /2
System.out.println(18>>3);//输出为2 

```
`>>>` (无符号右移)  无符号右移，忽略符号位，空位都以0补齐
正数做>>>运算的时候和>>是一样的。区别在于负数运算
```java
System.out.println("16>>>2运算的结果是 :"+((16)>>>2));//输出为4


System.out.println("-16>>>2运算的结果是 :"+((-16)>>>2));//输出为1073741820

```
```java
A= 0011 1100
B= 0000 1101

A&B = 0000 1100
A|B = 0011 1101
A^B = 0011 0001
~B = 1111 0010
```



- 在判断语句中，用 | 还是 ||，& 还是 &&
   - & 和 && 在判断语句中都可以实现“和”这个功能，不过区别在于 & 两边都运算，而 && 先算 && 左侧，若左侧为 false 那么右侧就不运算了


## 混合赋值运算符

[代码示例](https://www.cnblogs.com/niuyaomin/p/11732997.html)

|名称|简写形式|含义|
|-|-|-|
|赋值（Assignment）|x = y|x = y|
|加赋值（Addition assignment）|x += y|x = x + y|
|减赋值（Subtraction assignment）|x -= y|x = x - y|
|乘赋值（Multiplication assigment）|x *= y|x = x * y|
|除赋值（Division assignment）|x /= y|x = x / y|
|模赋值（Remainder assignment）|x %= y|x = x % y|
|指数赋值（Exponentiation assignment）|x **= y|x = x ** y|
|左移赋值（Left shift assignment）|x <<= y|x = x << y|
|右移赋值（Right shift assignment）|x >>= y|x = x >> y|
|无符号右移赋值（Unsigned right shift assignment）|x >>>= y|x = x >>> y|
|按位与赋值（Bitwise AND assignment）|x &= y|x = x & y|
|按位异或赋值（Bitwise XOR assignment）|x ^= y|x = x ^ y|
|按位或赋值（Bitwise OR assignment）|x \|= y|x = x \| y|

## 字符串连接符 `+`
- 做加法时若出现String型，就会将数值转换为Sting型，进行拼接

[示例](https://blog.csdn.net/NONINETEEN/article/details/83065151)

```JAVA
 /**
 * 字符型变量初始值是字符
 * 结论：
 * 当输出语句中没有拼接“”时，字符型变量被赋值什么就输出什么；
 * 当“”前有2个及2个以上的字符型变量时，转化为int类型进行计算后输出；
 * 当“”前有1个或者0个字符型变量时，整个输出语句都转化成字符串类型后输出；
 */
char ch1 = 'A';
char ch2 = 'B';
// 初始值是什么就输出什么
System.out.println(ch1);    // A
// 先转化为int类型，进行计算
System.out.println(ch1+ ch2);                 // 131
// 先转化为int类型，进行计算
System.out.println(ch1+ ch2 + "");            // 131
// ""双引号前先转化为int类型，进行计算，""双引号后转化为字符串类型
System.out.println(ch1+ ch2 + "" + 'C');      // 131C
// ""双引号前后都转化为字符串
System.out.println(ch1 + "" + ch2 + 'C');     // ABC
// ""双引号前后都转化为字符串
System.out.println(ch1 + "" + ch2);           // AB
// ""双引号后都转化为字符串
System.out.println("" + ch1+ ch2);            // AB
/**
 * 字符型变量初始值是字符
 * 结论：
 * 当输出语句中没有拼接“”时，字符型变量被赋值什么就输出什么；
 * 当“”前有2个及2个以上的字符型变量时，转化为int类型进行计算后输出；
 * 当“”前有1个或者0个字符型变量时，整个输出语句都转化成字符串类型后输出；
 */
ch1 = 65;
ch2 = 66;
char ch3 = 67;
// 初始值什么就输出什么
System.out.println(ch1);  // 65
// ""双引号前先转化为int类型，进行计算后输出
System.out.println(ch1 + ch2 + "");          // 131
// ""双引号前转化为字符类型输出
System.out.println( ch1 + "");               // A
// ""双引号前先转化为int类型，进行计算，""双引号后转化为字符串类型
System.out.println(ch1 + ch2 + "" + ch3);    // 131C
// ""双引号前后都转化为字符串
System.out.println(ch3 + "" + ch1 + ch2);    // CAB         
				   /**
 * 拼接对象是字符串时，结果和字符型变量初始值是字符相同的结果
 * 结论：
 * 当输出语句中没有拼接“”时，字符型变量被赋值什么就输出什么；
 * 当“”前有2个及2个以上的字符型变量时，转化为int类型进行计算后输出；
 * 当“”前有1个或者0个字符型变量时，整个输出语句都转化成字符串类型后输出；
 */
int a = 1, b = 2 ;
String c = "3";
System.out.println(a + b + c );             // 33
System.out.println(c + a + b);              // 312

```

## 条件运算符
`?:`:三元运算符`x?y:z`，运算规则是从右往左 ，如果 x == true,则结果为 y, 否则结果为 z
```java

int score = 80;
String grade = score < 60?"不及格":"及格"; 
//如果score< 60,则结果为不及格, 否则结果为及格
System.out.println(grade);   //及格

////多级计算，从右往左
//op1 ? op2 : op3 ? op4 : op5
//优先计算op3 ? op4 : op5
int score = 11;
String grade = score > 80 ? "优秀" : score > 60 ? "及格" : "不及格";
//先执行score > 60 ? "及格" : "不及格"；判断是否及格，若<=60直接输出不及格,
//否则执行score > 80 ? "优秀" : "及格"进行判断
```