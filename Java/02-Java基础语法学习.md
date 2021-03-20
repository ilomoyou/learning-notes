# 注释

Java中的注释有三种：

- 单行注释

  只能注释一行文字

- 多行注释

  可以注释一段文字

- 文档注释

```java
// 我是单行注释

/*
我是多行注释
我是多行注释
我是多行 注释
 */

/**
 * JavaDoc：文档注释
 * @Author 张三
 * @Description Hello World
 */
```

# 标识符和关键字

**关键字：**

![image-20210311185221247](02-Java%E5%9F%BA%E7%A1%80%E8%AF%AD%E6%B3%95%E5%AD%A6%E4%B9%A0.assets/image-20210311185221247.png)

**标识符：**

***Java 中所有的组成部分都需要名字。类名、变量名以及方法名都被称为标识符。***

注意点：

- 所有的标识符都应该以字母（A-Z 或者 a-z）、美元符（$）、或者下划线（_）开始
- 首字符之后可以是字母（A-Z 或者 a-z）、美元符（$）、下划线（_）或数字的任何字符组合
- 不能使用关键字作为变量名或方法名
- 标识符是**大小写敏感**的

# 数据类型

**强类型语言**

要求变量的使用要严格符合规定，所有的变量都必须先定义后才能使用

**弱类型语言**

弱类型语言也称为弱类型定义语言。与强类型定义相反。像vb，php，javascript，python，vbscript等就属于弱类型语言。

例如：在vbscript中，可以将字符串 12 和整数 3 进行连接得到字符串 123，然后可以把它看成整数 123，而不需要显式转换

**区别**：

弱类型的语言的东西没有明显的类型，他能随着环境的不同，自动变换类型

而强类型则没这样的规定，不同类型间的操作有严格定义，只有相同类型的变量才能操作。虽然系统也有一定的默认转换，但绝没有弱类型那么随便

**Java的数据类型分为两大类**

1. ***基本类型***（primitive type）
2. ***引用类型***（reference type）

![](02-Java%E5%9F%BA%E7%A1%80%E8%AF%AD%E6%B3%95%E5%AD%A6%E4%B9%A0.assets/java数据类型.png)**什么是字节：**

- 位（bit）：是计算机***内部数据*** 储存的最小单位，11001100 是一个八位二进制数
- 字节（byte）：是计算机中***数据处理*** 的基本单位，习惯上用大写 B 来表示
- 1B （byte，字节）= 8bit（位）
- 字符：是指计算机中使用的字母、数字、字和字符



- 1bit 表示 1位
- 1Byte 表示一个字节 1B = 8b
- 1024B = 1KB
- 1024KB = 1M
- 1024M = 1G

# 数据类型扩展及面试题讲解

```java
public class Demo01 {
    public static void main(String[] args) {
        // 进制拓展
        int num = 10;    // 整数
        int num2 = 0b10; // 二进制 0b
        int num3 = 010;  // 八进制 0
        int num4 = 0x10; // 十六进制 0x
        System.out.println(num);  // 10
        System.out.println(num2); // 2
        System.out.println(num3); // 8
        System.out.println(num4); // 16

        // 浮点数 有限、离散 舍入误差 大约、接近但不等于
        // 最好完全避免使用浮点数进行比较
        // 可用 BigDecimal 数学工具类 进行比较
        float f = 0.1f;
        double d = 1.0/10;
        System.out.println(f); // 0.1
        System.out.println(d); // 0.1
        System.out.println(f == d);  // false

        float f1 = 213131313131f;
        float f2 = f1 + 1;
        System.out.println(f1 == f2);  // true

        // 字符拓展
        // (int) 强制转换为int
        // 所有的字符本质还是数字，经过了 Unicode 编码
        char c1 ='A';
        char c2 = '中';
        char c3 = '\u0061';
        System.out.println(c1);      // A
        System.out.println((int)c1); // 65
        System.out.println(c2);      // 中
        System.out.println((int)c2); // 20013
        System.out.println(c3);      // a

        // 转义字符
        // \t 制表符
        // \n 换行
        // ...
        System.out.println("Hello\tWorld");
        System.out.println("Hello\nWorld");

        // 对象 从内存分析
        String sa = "hello world";
        String sb = "hello world";
        System.out.println(sa == sb); // true

        String sc = new String("hello world");
        String sd = new String("hello world");
        System.out.println(sc == sd); // false
    }
}
```

# 类型转换

- **由于 Java 是强类型语言，所以在进行有些运算的时候，需要用到类型转行**

![image-20210312155731782](02-Java%E5%9F%BA%E7%A1%80%E8%AF%AD%E6%B3%95%E5%AD%A6%E4%B9%A0.assets/image-20210312155731782.png)

- **运算中，不同类型的数据先转为同一类型，然再进行计算**
- **强制类型转换**（高 -- 低）
- **自动类型转换**（低 -- 高）

```java
public class Demo02 {
    public static void main(String[] args) {
        int i = 128;
        // 强制转换 (类型)变量名 高--低
        byte b = (byte)i; // 内存溢出，byte取值范围：-128-127
        System.out.println(b); // -128
        // 自动转换 低--高
        double d = i;
        System.out.println(d); // 128.0

        /*
        注意点：
        1. 不能对布尔值进行转换
        2. 不能把对象类型转换为不相干的类型
        3. 高容量转换到低容量时，强制转换
        4. 转换时可能存在内存溢出，或精度问题
         */

        // 精度问题
        System.out.println((int)22.6);  // 22
        System.out.println((int)-46.6); // -46

        // 自动转换
        char c = 'a';
        int num = c + 1;
        System.out.println(num); // 98
        System.out.println((char)num); // b

        // 操作比较大的数值时，注意溢出问题
        int money = 10_0000_0000;
        int years = 20;
        int total = money * years;
        System.out.println(total); // -1474836480，计算时溢出了
        long total2 = money * years;
        System.out.println(total2); // 同上结果 默认是 int，转换之前已经存在问题

        long total3 = money*((long)years); // 先把一个数转换为 long
        System.out.println(total3); // 20000000000
    }
}
```

# 变量、常量、作用域

## 变量

- 变量是什么：就是可以变化的量！
- Java 是一种强类型语言，每个变量都必须声明其类型
- Java 变量是程序中最基本的存储单元，其要素包括变量名，变量类型和作用域

![image-20210312164753352](02-Java%E5%9F%BA%E7%A1%80%E8%AF%AD%E6%B3%95%E5%AD%A6%E4%B9%A0.assets/image-20210312164753352.png)

注意事项：

- 每个变量都有类型，类型可以是基本类型，也可以是引用类型
- 变量名必须是合法的标识符
- 变量声明是一条完整的语句，因此每一个声明都必须以分号结束

## 变量作用域

- **类变量**
- **实例变量**
- **局部变量**

![image-20210312165900161](02-Java%E5%9F%BA%E7%A1%80%E8%AF%AD%E6%B3%95%E5%AD%A6%E4%B9%A0.assets/image-20210312165900161.png)

## 常量

- 常量（Constant）：初始化（initialize）后不能再改变的值，不会变动的值

- 所谓常量可以理解成一种特殊的变量，它的值被设定后，在程序运行过程中不允许被该表

  ```java
  final 常量名 = 值;
  final double PI = 3.14;
  ```

- 常量名一般使用大写字符

变量的命名规范：

- 所有的变量、方法、类名：见名知意
- 类成员变量：首字母小写和驼峰原则：monthSalary
- 局部变量：首字母小写和驼峰原则
- 常量：大写字母和下划线：MAX_VALUE
- 类名：首字母大写和驼峰原则：Man，GoodMan
- 方法名：首字母小写和驼峰原则：run()，runRun()

# 运算符

Java 语言支持如下运算符：

- 算术运算符：+，-，*，/，%，++，--
- 赋值运算符：=
- 关系运算符：>，<，>=，<=，==，!=，instanceof
- 逻辑运算符：&&，||，!（与或非）
- 位运算符：&，|，^，~，>>，<<，>>> （了解即可）
- 条件运算符：? :
- 扩展赋值运算符：+=，-=，*=，/=

```java
package operator;

public class Demo01 {
    public static void main(String[] args) {
        // ++ -- 自增、自减 一元运算符
        int a = 3;
        int b = a++; // 执行完这行代码后，先给b赋值，再自增
        // a++ a = a + 1
        System.out.println(a); // 4
        // ++a a = a + 1
        int c = ++a; // 执行完这行代码后，先自增，再给c赋值
        System.out.println(a); // 5
        System.out.println(b); // 3
        System.out.println(c); // 5

        // 幂运算 2^3 2*2*2 = 8
        // 很多运算可以借助一些工具类来实现
        double pow = Math.pow(2, 3);
        System.out.println(pow); // 8.0
    }
}
```

```java
package operator;

public class Demo02 {
    public static void main(String[] args) {
        // 与（and） 或（or） 非（取反）
        boolean a = true;
        boolean b = false;

        System.out.println(a && b);     // false 逻辑与：两个变量都为真，结果则为真
        System.out.println(a || b);     // true 逻辑或：两个变量有一个为真，结果则为真
        System.out.println(!(a && b));  // true 逻辑非：如果是真则为假，如果是假则为真

        // 短路运算
        int c = 5;
        boolean d = c < 4 && c++ < 4;
        System.out.println(d); // false
        System.out.println(c); // 5 前面的表达式(c < 4)为 false，后面的表达式(c++ < 4)将不再执行

        // 位运算
        /*
        A = 0011 1100
        B = 0000 1101

        A&B = 0000 1100 // 与，如果相对应位都是1，则结果为1，否则为0
        A|B = 0011 1101 // 或，如果相对应位都是 0，则结果为 0，否则为 1
        A^B = 0011 0001 // 异或，如果相对应位值相同，则结果为0，否则为1
        ~B = 1111 0010 // 取反，按位取反运算符翻转操作数的每一位，即0变成1，1变成0
         */

        // 2 * 8 怎么计算最快 可拆分为 2*2*2*2
        // << 左移 相当于 *2
        // >> 右移 相当于 /2
        // >>> 表示无符号右移，也叫逻辑右移
        System.out.println(2 << 3); // 16
    }
}
```

```java
package operator;

public class Demo03 {
    public static void main(String[] args) {
        int a = 10;
        int b = 20;

        // 扩展赋值运算符
        a += b; // a = a + b
        a -= b; // a = a - b
        System.out.println(a); // 10

        // 字符串连接符 +
        System.out.println(a + b); // 30
        // 面试题，字符串在前在后的区别
        System.out.println("" + a + b); // 1020
        System.out.println(a + b + ""); // 30
    }
}
```

```java
package operator;

public class Demo04 {
    public static void main(String[] args) {
        // x ? y : z
        // 如果 x == true，则为 y，否则为 z
        int score = 80;
        String type = score < 60 ? "不及格" : "及格";
        System.out.println(type); // 及格
    }
}
```

**优先级：**

| 类别     | 操作符                                     | 关联性   |
| :------- | :----------------------------------------- | :------- |
| 后缀     | () [] . (点操作符)                         | 左到右   |
| 一元     | expr++ expr--                              | 从左到右 |
| 一元     | ++expr --expr + - ～ ！                    | 从右到左 |
| 乘性     | * /％                                      | 左到右   |
| 加性     | + -                                        | 左到右   |
| 移位     | >> >>>  <<                                 | 左到右   |
| 关系     | > >= < <=                                  | 左到右   |
| 相等     | == !=                                      | 左到右   |
| 按位与   | ＆                                         | 左到右   |
| 按位异或 | ^                                          | 左到右   |
| 按位或   | \|                                         | 左到右   |
| 逻辑与   | &&                                         | 左到右   |
| 逻辑或   | \| \|                                      | 左到右   |
| 条件     | ？：                                       | 从右到左 |
| 赋值     | = + = - = * = / =％= >> = << =＆= ^ = \| = | 从右到左 |
| 逗号     | ，                                         | 左到右   |

# 包机制

- 为了更好地组织类，Java 提供了包机制，用于区别类名的命名空间

- 包语句的语法格式为：

  ```java
  package pkg1[. pkg2[. pkg3...]];
  ```

- **一般利用公司域名倒置作为包名**

- 为了能够使用某一个包的成员，我们需要在 Java 程序中明确导入该包。使用 “import” 语句可完成此功能

  ```java
  import package1[.package2...].(classname|*);
  ```

# JavaDoc

- javadoc 命令是用来生成自己的API文档的

  ```bash
  # javadoc 参数 java文件名
  javadoc -encoding UTF-8 -charset UTF-8 HelloWorld.java
  ```

- 参数信息

  - @author 作者名
  - @version 版本号
  - @since 指明需要最早使用的jdk版本
  - @param 参数名
  - @return 返回值情况
  - @throws 异常抛出情况

