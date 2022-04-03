---
title: SpringBoot02:配置文件
date: 2021-06-13 20:17:36
tags: [Java,学习笔记,SpringBoot]
categories: 
  - Study Notes
  - SpringBoot
excerpt: SpringBoot的配置文件
---


# SpringBoot的配置

## 配置文件的分类

SpringBoot是基于约定的，所以很多配置都有默认值,但如果想使用自己的配置替换默认配置的话，就可以使用application.properties或者application.yml（application.yaml）进行配置。

SpringBoot默认会从Resources目录下加载application.properties或application.yml（application.yaml）文件

- properties
``` properties
> server.port=8081
```
- yml(yaml)
``` yml
server: 
  port: 8081
```

## 加载优先级

若Resources目录下`application.properties`,`application.yml`,`application.yaml`三个文件同时存在，
将会以`properties`>`yml`>`yaml`的优先级进行加载，低优先级配置文件若存在与高优先级配置文件相同的属性则会被忽略，若低优先级配置文件中的属性若在高优先级配置文件中没有则会被识别

> application.properties
``` properties
server.port=8081
```

> application.yml
``` yml
server: 
  port: 8082
name1: abc
```

> application.yaml
``` yaml
server: 
  port: 8083
name1: abc1
name2: abc2
```
- 最终端口号将为`8081`
- `application.yml`中的`name1: abc`会被识别
- `application.yaml`中的`name2: abc2`会被识别,`name1: abc1`会被忽略

## YAML

YML文件格式是YAML (YAML Aint Markup Language)编写的文件格式，YAML是一种直观的能够被电脑识别的的数据数据序列化格式，并且容易被人类阅读，容易和脚本语言交互的，可以被支持YAML库的不同的编程语言程序导入，比如： C/C++, Ruby, Python, Java, Perl, C#, PHP等。YML文件是以数据为核心的，比传统的xml方式更加简洁

YML文件的扩展名可以使用.yml或者.yaml

### 基本语法

- 大小写敏感
- 数值前面（冒号后面）必须有空格作为分隔符（以冒号结尾不需要空格，表示文件路径的模版可以不需要空格）
- 使用固定的缩进风格表示层级关系，不要使用TAB(不同IDE中TAB对应的空格目数不同，会导致层级混乱)
- `#`表示注释

### 数据格式

#### 对象（map）：键值对的集合

```yaml
person:
  name: zhangsan

##行内写法
person: {name: zhangsan}  
```

#### 数组：一嘴按次序排列的值

```yaml
address:
  - beijing
  - shanghai

##行内写法  
address: [beijing,shanghai]
```

#### 纯量：单个的、不可再分的值

```yaml
msg1: 'hello \n world' # 单引忽略转义字符,原样输出
msg1: "hello \n world" # 双引识别转义字符
```

#### 参数引用
 引用上边定义的值

 ```yaml
name: zhangsan
person:
name: ${name} # 引用上边定义的name值
```

## 读取配置内容


- 配置内容
```yaml

###对象
person:
  name: zhangsan

###数组
address:
  - beijing
  - shanghai

#### 纯量
msg1: 'hello \n world' # 单引忽略转义字符,原样输出
msg1: "hello \n world" # 双引识别转义字符  
#### 参数引用
name: zhangsan
person1:
name: ${name} # 引用上边定义的name值
```
### @Value

### Environment

### @ConfigurationProperties