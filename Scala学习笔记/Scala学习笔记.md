# Scala学习笔记

[TOC]



## 概述

`Scala` 是 `Scalable Language` 的简写，是一门`多范式`的编程语言

`Scala`是一门现代的`多范式语言`，志在以简洁、优雅及类型安全的方式来表达常用的编程模型。它平滑地集成了`面向对象`和`函数式语言`的特性。

## Scala 特性：

面向对象、函数式编程、静态类型、扩展性、并发性、互操作性

[scala官方文档]: https://docs.scala-lang.org/zh-cn/tour/tour-of-scala.html

Scala配备了一个拥有强大表达能力的类型系统，它可以静态地强制以安全、一致的方式使用抽象。典型来说，这个类型系统支持：

- [泛型类](https://docs.scala-lang.org/zh-cn/tour/generic-classes.html)
- [型变注解](https://docs.scala-lang.org/zh-cn/tour/variances.html)
- [上](https://docs.scala-lang.org/zh-cn/tour/upper-type-bounds.html)、[下](https://docs.scala-lang.org/zh-cn/tour/lower-type-bounds.html) 类型边界
- 作为对象成员的[内部类](https://docs.scala-lang.org/zh-cn/tour/inner-classes.html)和[抽象类型](https://docs.scala-lang.org/zh-cn/tour/abstract-type-members.html)
- [复合类型](https://docs.scala-lang.org/zh-cn/tour/compound-types.html)
- [显式类型的自我引用](https://docs.scala-lang.org/zh-cn/tour/self-types.html)
- [隐式参数](https://docs.scala-lang.org/zh-cn/tour/implicit-parameters.html)和[隐式转化](https://docs.scala-lang.org/zh-cn/tour/implicit-conversions.html)
- [多态方法](https://docs.scala-lang.org/zh-cn/tour/polymorphic-methods.html)

[类型推断](https://docs.scala-lang.org/zh-cn/tour/type-inference.html)让用户不需要标明额外的类型信息。这些特性结合起来为安全可重用的编程抽象以及类型安全的扩展提供了强大的基础。

## Scala 语言特点：

`Scala`是一门以Java虚拟机（JVM）为运行环境并将面向对象和函数式编程的最佳特性结合在一起的

静态类型编程语言（静态语言需要提前编译的如：`Java`、`c`、`c++`等，动态语言如：`js`）。 

1）Scala是一门`多范式`的编程语言，Scala支持`面向对象`和`函数式编程`。（`多范式`，就是多种编程方

法的意思。有`面向过程`、`面向对象`、`泛型`、`函数式`四种程序设计方法。） 

2）Scala源代码（.scala）会被编译成Java字节码（.class），然后运行于JVM之上，并可以调用现有

的Java类库,实现两种语言的无缝对接。 

3）Scala单作为一门语言来看，非常的简洁高效**。** 



```scala
object Hello {
	def main(args: Array[String]): Unit = {
		println("hello scala")
	}
}
Scala完全面向对象，故Scala去掉了Java中非面向对象的元素，如static关键字，void类型

1）static

Scala无static关键字，由object实现类似静态方法的功能（类名.方法名）。

2）void
对于无返回值的函数，Scala定义其返回值类型为Unit类
```





## Scala程序反编译:

```scala
1）Hello源代码
object Hello {
	def main(args: Array[String]): Unit = {
		println("hello,scala")
	} 
}
2）Hello.class类
public final class Hello{
	public static void main(String[] paramArrayOfString) {
		Hello$.MODULE$.main(paramArrayOfString);
    }
}
3）Hello$.class类
public final class Hello$ {
	public static final MODULE$;
static
	{
		new (); 
	}
public void main(String[] args) {
	Predef..MODULE$.println("hello,scala"); }
	private Hello$(){
		MODULE$ = this;
    }
}
（1）Object编译后生成Hello$.class和Hello.class两个文件
（2）Hello中有个main函数，调用 Hello$ 类的一个静态对象MODULES$
（3）Hello$.MODULE$. 对象是静态的，通过该对象调用Hello$的main函数
```



## 注释

```scala
// Hello Scala 单行注释

/*
*多行注释
*Hello Scala
*Hello Scala
*/

/**
文档注释
*/
```



## Scala 包

### 定义包

Scala 使用 package 关键字定义包，在Scala将代码定义到某个包中有两种方式：

第一种方法和 Java 一样，在文件的头定义包名，这种方法就后续所有代码都放在该包中。 比如：

```
package com.runoob
class HelloWorld
```

第二种方法有些类似 C#，如：

```
package com.runoob {
  class HelloWorld 
}
```

第二种方法，可以在一个文件中定义多个包。

### 引用

Scala 使用 import 关键字引用包。

```
import java.awt.Color  // 引入Color
 
import java.awt._  // 引入包内所有成员
 
def handler(evt: event.ActionEvent) { // java.awt.event.ActionEvent
  ...  // 因为引入了java.awt，所以可以省去前面的部分
}
```

import语句可以出现在任何地方，而不是只能在文件顶部。import的效果从开始延伸到语句块的结束。这可以大幅减少名称冲突的可能性。

如果想要引入包中的几个成员，可以使用selector（选取器）：

```
import java.awt.{Color, Font}
 
// 重命名成员
import java.util.{HashMap => JavaHashMap}
 
// 隐藏成员
import java.util.{HashMap => _, _} // 引入了util包的所有成员，但是HashMap被隐藏了
```

> **注意：**默认情况下，Scala 总会引入 java.lang._ 、 scala._ 和 Predef._，这里也能解释，为什么以scala开头的包，在使用时都是省去scala.的。



## 基本语法

- Scala区分大小写，所以说标识符Hello和hello在Scala中会有不同的含义

- 类名：首字母大写，如果需要使用几个单词来构成一个类的名称，每个单词的第一个字母要大写   `class MyFirstScalaClass`。
- 方法名： 所有的方法名称的第一个字母用小写，如果若干单词被用于构成方法的名称，则每个单词的第一个字母应大写  `def myMethodName()`。
- 对象名应与文件名匹配。保存文件时，应该保存它使用的对象名称（记住Scala是区分大小写），并追加".scala"为文件扩展名。 （如果文件名和对象名称不匹配，程序将无法编译）。
- `def main(args: Array[String])` - Scala程序从main()方法开始处理，这是每一个Scala程序的强制程序入口部分。

### 标识符的命名规范

Scala 对各种`变量`、`方法`、`函数`等命名时使用的字符序列称为标识符。即：凡是自己可以起名字的地方都叫标识符。

- 以字母或者下划线开头，后接字母、数字、下划线

```scala
val hello: String = ""
var Hello123 = ""
val _abc = 123
```



- 以操作符开头，且只包含操作符（+ - * / # !等）

```scala
val -+*/% = "Hello"
println(-+*/%)
```



- 用反引号\`....`包括的任意字符串，即使是 Scala 关键字（39 个）也可以

  ```scala
  var `if` = "if"
  println(`if`)
  ```

| abstract  | case     | catch    | class   |
| --------- | -------- | -------- | ------- |
| def       | do       | else     | extends |
| false     | final    | finally  | for     |
| forSome   | if       | implicit | import  |
| lazy      | match    | new      | null    |
| object    | override | package  | private |
| protected | return   | sealed   | super   |
| this      | throw    | trait    | try     |
| true      | type     | val      | var     |
| while     | with     | yield    |         |
| -         | :        | =        | =>      |
| <-        | <:       | <%       | >:      |
| #         | @        |          |         |



## 变量和常量

- 一、变量（`variable`）： 在程序运行过程中其值可能发生改变的量叫做变量。如：时间，年龄。

- 二、常量（`Values`）：在程序运行过程中其值不会发生变化的量叫做常量。如：数值 3，字符'A'。

  

  ==在 Scala 中，使用关键词 **"var"** 声明变量，使用关键词 **"val"** 声明常量。==

声明变量实例如下：

```scala
var myVar : String = "Hello"
var myVar : String = "Scala"
```

以上定义了变量 myVar，我们可以修改它。

声明常量实例如下：

```scala
val myVal : String = "hh"
myval = "hello" //报错
```

以上定义了常量 myVal，它是不能修改的。如果程序尝试修改常量 myVal 的值，程序将会在编译时报错。

## 代码块（Blocks）

你可以组合几个表达式，并且用`{}`包围起来。我们称之为代码块（block）。

代码块中最后一个表达式的结果，也正是整个块的结果。

```scala
println({
  val x = 1 + 1
  x + 1
}) // 3
```

## 变量类型声明	

变量的类型在变量名之后等号之前声明。定义变量的类型的语法格式如下：

```scala
var VariableName : DataType [=  Initial Value]

或

val VariableName : DataType [=  Initial Value]
```



==声明变量时，类型可以省略，编译器自动推导，即类型推导==

```scala
var age = 20
age = 30
```

==类型确定后，就不能修改，说明 Scala 是强数据类型语言==

```scala
age = "hello" //错误
```

==变量声明时，必须要有初始值==

```scala
var name //错误
```

==在声明/定义一个变量时，可以使用 var 或者 val 来修饰，var 修饰的变量可改变，val 修饰的变量不可改==



==var 修饰的对象引用可以改变，val 修饰的对象则不可改变，但对象的状态（值）却是可以改变的。（比如：自定义对象、数组、集合等等）==

```scala
object TestVar {
 	def main(args: Array[String]): Unit = {
 	// p1 是 var 修饰的，p1 的属性可以变，而且 p1 本身也可以变
 	var p1 = new Person()
 	p1.name = "jojo"
 	p1 = null
 	// p2 是 val 修饰的，那么 p2 本身就不可变（即 p2 的内存地址不能变），但是，p2 的属性是可以变，因为属性并没有用 val 修饰。
 	val p2 = new Person()
 	p2.name="yoyo"
	// p2 = null // 错误的，因为 p2 是 val 修饰的
	 }
}
class Person{
	var name : String = "yoyo"
}
```



## Scala 数据类型

![Scala Type Hierarchy](https://docs.scala-lang.org/resources/images/tour/unified-types-diagram.svg)![image-20211130113806068](../../../AppData/Roaming/Typora/typora-user-images/image-20211130113806068.png)

Scala 与 Java有着相同的数据类型，下表列出了 Scala 支持的数据类型：

| 数据类型 | 描述                                                         |
| :------- | :----------------------------------------------------------- |
| Byte     | 8位有符号补码整数。数值区间为 -128 到 127                    |
| Short    | 16位有符号补码整数。数值区间为 -32768 到 32767               |
| Int      | 32位有符号补码整数。数值区间为 -2147483648 到 2147483647     |
| Long     | 64位有符号补码整数。数值区间为 -9223372036854775808 到 9223372036854775807 |
| Float    | 32 位, IEEE 754 标准的单精度浮点数                           |
| Double   | 64 位 IEEE 754 标准的双精度浮点数                            |
| Char     | 16位无符号Unicode字符, 区间值为 U+0000 到 U+FFFF             |
| String   | 字符序列                                                     |
| Boolean  | true或false                                                  |
| Unit     | 表示无值，和其他语言中void等同。用作不返回任何结果的方法的结果类型。Unit只有一个实例值，写成()。 |
| Null     | null 或空引用                                                |
| Nothing  | Nothing类型在Scala的类层级的最底端；它是任何其他类型的子类型。当一个函数，我们确认没有正常的返回值，可以用Nothing来指定返回类型，这样有一个好处，就是我们可以把返回的值（异常）赋给其他的函数或者变量（兼容性） |
| Any      | Any是所有其他类的超类                                        |
| AnyRef   | AnyRef类是Scala里所有引用类(reference class)的基类           |

上表中列出的数据类型都是对象，也就是说scala没有java中的原生类型。在scala是可以对数字等基础类型调用方法的。



### Nothing和Null

`Nothing`是所有类型的子类型，也称为底部类型。没有一个值是`Nothing`类型的。它的用途之一是给出非正常终止的信号，如抛出异常、程序退出或者一个无限循环（可以理解为它是一个不对值进行定义的表达式的类型，或者是一个不能正常返回的方法）。

`Null`是所有引用类型的子类型（即`AnyRef`的任意子类型）。它有一个单例值由关键字`null`所定义。`Null`主要是使得Scala满足和其他JVM语言的互操作性，但是几乎不应该在Scala代码中使用。我们将在后面的章节中介绍`null`的替代方案。



### 数值类型自动转换

当 Scala 程序在进行赋值或者运算时，精度小的类型自动转换为精度大的数值类型，这 个就是自动类型转换（隐式转换）。数据类型按精度（容量）大小排序为：

![image-20211130093222491](../../../AppData/Roaming/Typora/typora-user-images/image-20211130093222491.png)

```scala
//（1）自动提升原则：有多种类型的数据混合运算时，系统首先自动将所有数据转换成精度大的那种数据类型，然后再进行计算。

//（2）把精度大的数值类型赋值给精度小的数值类型时，就会报错，反之就会进行自动类型转换。

//（3）(`byte`，`short`)和 `char`之间不会相互自动转换。

//（4）`byte`，`short`，`char` 他们三者可以计算，在计算时首先转换为 `int` 类型。 
```



### 强制类型转换

#### 基本说明

==自动类型转换的逆过程，将精度大的数值类型转换为精度小的数值类型。使用时要加上强制转函数，但可能造成精度降低或溢出，格外要注意。==

```scala
Java : int num = (int)2.5
Scala : var num : Int = 2.7.toInt
```



### 回顾：Java数据类型

- Java基本类型：char、byte、short、int、long、float、double、boolean

- Java引用类型：（对象类型）

由于Java有基本类型，而且基本类型不是真正意义的对象，即使后面产生了基本类型的包装类，但是仍然存在基本数据类型，所以Java语言并不是真正意思的面向对象。

- Java基本类型的包装类：Character、Byte、Short、Integer、Long、Float、Double、Boolean

注意：Java中基本类型和引用类型没有共同的祖先。

---

1）Scala中一切数据都是对象，都是Any的子类。 

2）Scala中数据类型分为两大类：数值类型（AnyVal）、引用类型（AnyRef），不管是值类型还是引用类型都是

对象。 

3）Scala数据类型仍然遵守，低精度的值类型向高精度值类型，自动转换（隐式转换）

4）Scala中的StringOps是对Java中的String增强

5）Unit：对应Java中的void，用于方法返回值的位置，表示方法没有返回值。Unit是 一个数据类型，只有一个对象就是()。Void不是数据类型，只是一个关键字	

6）Null是一个类型，只 有一个对 象就 是null。它是所有引用类型（AnyRef）的子类。 

7）Nothing，是所有数据类型的子类，主要用在一个函数没有明确返回值时使 

用，因为这样我们可以把抛出的返回值，返回给任何的变量或者函数。

![Scala Type Hierarchy](https://docs.scala-lang.org/resources/images/tour/unified-types-diagram.svg)





## Scala 转义字符 

下表列出了常见的转义字符：

| 转义字符 | Unicode | 描述                                |
| :------- | :------ | :---------------------------------- |
| \b       | \u0008  | 退格(BS) ，将当前位置移到前一列     |
| \t       | \u0009  | 水平制表(HT) （跳到下一个TAB位置）  |
| \n       | \u000a  | 换行(LF) ，将当前位置移到下一行开头 |
| \f       | \u000c  | 换页(FF)，将当前位置移到下页开头    |
| \r       | \u000d  | 回车(CR) ，将当前位置移到本行开头   |
| \"       | \u0022  | 代表一个双引号(")字符               |
| \'       | \u0027  | 代表一个单引号（'）字符             |
| \\       | \u005c  | 代表一个反斜线字符 '\'              |

0 到 255 间的 Unicode 字符可以用一个八进制转义序列来表示，即反斜线‟\‟后跟 最多三个八进制。

在字符或字符串中，反斜线和后面的字符序列不能构成一个合法的转义序列将会导致 编译错误。



## 字符串输出

- 字符串，通过`+`连接

  ```scala
  val name : String = "alice"
  val age : Int = 18
  println(age + "岁的" + name + "在尚硅谷学习")
  ```

- `printf`：字符串，通过`%`传值

  ```scala
  printf("%d岁的%s在尚硅谷学习",age, name)
  ```

- 字符串模板（插值字符串）：通过$获取变量值

  ```scala
  println('\n' + s"${age}岁的${name}在尚硅谷学习")
  ```

- `*`可以将一个字符串复制多次并拼接

  ```scala
  println((name + '\t') * 3)
  ```

- `"""`三引号表示字符串，保持多行字符串的原始格式输出

  - 多行字符串，在** **Scala****中，利用三个双引号包围多行字符串就可以实现。

    输入的内容，带有`空格`、`\t` 之类，导致每一行的开始位置不能整洁对齐。

    应用 **scala** **的** **stripMargin** **方法，在** **scala** **中** **stripMargin** **默认**是`|`作为连接符,在多行换行的行头前面加一个`|`符号即可。

  ```scala
      val sql = s"""
         |select *
         |from
         |  student
         |where
         |  name = ${name}
         |and
         |  age > ${age}
         |""".stripMargin
      println(sql)
  ```



### 键盘输入

**在编程中，需要接收用户输入的数据，就可以使用键盘输入语句来获取。**

`StdIn.readLine()`、`StdIn.readShort()`、`StdIn.readDouble()`

```scala
import scala.io.StdIn
object TestInput {
 def main(args: Array[String]): Unit = {
 // 1 输入姓名
 println("input name:")
 var name = StdIn.readLine()
 // 2 输入年龄
 println("input age:")
 var age = StdIn.readShort()
 // 3 输入薪水
 println("input sal:")
 var sal = StdIn.readDouble()
 // 4 打印
 println("name=" + name)
 println("age=" + age)
 println("sal=" + sal)
 	}
}
```



### 文件输入输出

```scala
// 1、从文件中读取数据
Source.fromFile("../test.txt").foreach(print)
```

```scala
// 2、将数据写入文件
val writer  = new PrintWriter(new File("../output.txt"))
writer.write("hello scala from java writer")
writer.close()
```





## 运算符

