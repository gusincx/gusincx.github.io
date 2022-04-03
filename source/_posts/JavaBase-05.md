---
title: JavaBase_05:Scanner
date: 2021-05-03 14:06:12
tags: [Java,学习笔记]
categories: 
  - Study Notes
  - Java
---
看各种视频教程出来的大杂烩笔记，对他人作用估计不大。内容：Scanner
<!-- more -->

# 输入
# Scanner对象
## 基本语法

```java
Scanner sc = new Scanner(System.in)
```
## 获取输入数据

```java
sc.next();//读取到空白符就结束获取（剔除之前的空白符，并舍弃再一次遇到空白符之后的数据）
sc.nextLine();//读取整行数据，遇到"\n"就结束获取
sc.nextInt();//只能接受整型数据,空格/回车/制表符结束
```
|方法|返回值|开始读取字符(包括此字符)|停止读取字符(不包括此字符)|光标位置|
|-|-|-|-|-|
|next()|String|String|空格/回车/制表符|仍在本行|
|nextXxx()|基本数据类型xxx|xxx|空格/回车/制表符|仍在本行|
|nextLine()|String|任意字符|回车|移动到下一行起始位置|

- 判断是否还有输入的数据

```java
sc.hasNextInt();//扫描是否有Int型值，有着返回ture,若非Int类型则退出
sc.hasNext();//扫描是否有非空字符,如果有,则返回true,否则方法阻塞，等待输入内容然后继续扫描。
sc.hasNextLine();// 根据行匹配模式去扫描是否有值(包括空行),如果有,则返回true,否则方法阻塞，等待输入内容然后继续扫描。
```

## 判断输入数据

- hasNextInt()
  - 判断是否有Int型值，有着返回ture,若非Int类型则返回false

```java
public boolean hasNextInt(int radix) {
        setRadix(radix);
        boolean result = hasNext(integerPattern());
        if (result) { // Cache it
            try {
                String s = (matcher.group(SIMPLE_GROUP_INDEX) == null) ?
                    processIntegerToken(hasNextResult) :
                    hasNextResult;
                typeCache = Integer.parseInt(s, radix);
            } catch (NumberFormatException nfe) {
                result = false;
            }
        }
        return result;
    }
```
- hasNextLine()
  - 会根据行匹配模式去判断接下来是否有一行(包括空行)。如果有,则返回true,否则方法阻塞，等待输入内容然后继续扫描

```java
public boolean hasNextLine() {
        saveState();

        modCount++;
        String result = findWithinHorizon(linePattern(), 0);
        if (result != null) {
            MatchResult mr = this.match();
            String lineSep = mr.group(1);
            if (lineSep != null) {
                result = result.substring(0, result.length() -
                                          lineSep.length());
                cacheResult(result);

            } else {
                cacheResult();
            }
        }
        revertState();
        return (result != null);
```

- hasNext();
  - 先扫描缓冲区中是否有字符，有则返回true,继续扫描。直到扫描为空，这时并不返回false,而是将方法阻塞，等待输入内容然后继续扫描

```java
    public boolean hasNext() {
        ensureOpen();
        saveState();
        modCount++;
        while (!sourceClosed) {
            if (hasTokenInBuffer()) {
                return revertState(true);
            }
            readInput();
        }
        boolean result = hasTokenInBuffer();
        return revertState(result);
    }
```

[Scanner中hasNext()方法阻塞的解决方法](https://blog.csdn.net/gao_zhennan/article/details/80562548)

```java
import java.util.*;
public class ScannerTest {
    public static void main(String[] args)
    {
        System.out.println("请输入若干单词，以空格作为分隔");
        Scanner sc = new Scanner(System.in);
        while(!sc.hasNext("#"))  //匹配#返回true,然后取非运算。即以#为结束符号
        {
            System.out.println("键盘输入的内容是："+ sc.next());
        }
        System.out.println("out");
        sc.close();//属于io流的类不关闭会一直占用资源，使用完后需要关闭
    }
}
```

- hasNextDouble()方法的使用

```java
import java.util.*;
public class ScannerTest {
    public static void main(String[] args)
    {
        Scanner sc = new Scanner(System.in);
        Double sum = 0.0;
        int m = 0;
        while(sc.hasNextDouble())
        {
            double x = sc.nextDouble();
            m++;
            sum += x;
            System.out.println("输入了第"+m+"个数,当前sum="+sum);
        }

        System.out.println("输入了"+m+"个数,sum="+sum);
        System.out.println(+m+"个数的平均值为"+sum/m);
        sc.close();//属于io流的类不关闭会一直占用资源，使用完后需要关闭
    }
}
```