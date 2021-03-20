# Java三大版本

Write Once、Run Anywhere

- JavaSE：标准版，Java的基础和核心（桌面程序，控制台开发……）
- JavaME：微型版，或叫移动版，用于嵌入式开发。但是由于安卓和苹果的崛起，javaME也一步步地退出了舞台（手机，小家电……）
- JavaEE：企业版，是市场的主流，用于企业级应用程序的开发（web端，服务器开发……）

# JDK、JRE、JVM

JDK：Java Development Kit（Java开发工具包）

JRE：Java Runtime Environment（Java运行环境）

JVM：Java Virtual Machine（Java虚拟机）

![image-20210310183310414](01-Java%E5%85%A5%E9%97%A8%E5%8F%8A%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA.assets/image-20210310183310414.png)

***三者间的关系：简单来说就是 JDK 包含 JRE，JRE 又包含 JVM 的关系***

# JDK环境变量配置

- 新建系统变量：***JAVA_HOME***

![image-20210311154847918](01-Java%E5%85%A5%E9%97%A8%E5%8F%8A%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA.assets/image-20210311154847918.png)

- 新建Path变量：

1. ***%JAVA_HOME%\bin***
2. ***%JAVA_HOME%\jre\bin***

![image-20210311155056963](01-Java%E5%85%A5%E9%97%A8%E5%8F%8A%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA.assets/image-20210311155056963.png)

- cmd测试：***java -version***

![image-20210311144737731](01-Java%E5%85%A5%E9%97%A8%E5%8F%8A%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA.assets/image-20210311144737731.png)

# Hello World！

运行 Java 生涯中的第一个 hello world，发出程序员对这个世界的第一声呐喊！

- 新建名为：***Hello.java*** 文件

- 编写代码：

```java
public class Hello {
	public static void main(String[] args) {
		System.out.print("Hello, World!");
	}
}
```

- 使用 ***javac*** 命令编译 java 文件，会生成一个对应的 ***Hello.class*** 文件
- 使用 ***java*** 命令，运行 class 文件

![image-20210311161102020](01-Java%E5%85%A5%E9%97%A8%E5%8F%8A%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA.assets/image-20210311161102020.png)

![image-20210311160947530](01-Java%E5%85%A5%E9%97%A8%E5%8F%8A%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA.assets/image-20210311160947530.png)

- 成功输出 ***Hello, World!***

# Java程序运行机制

说到 Java 的运行机制，不得不提一下什么是编译型语言，什么是解释型语言。

- **编译型**

  编译型语言是先将源代码编译成机器语言（机器可以读懂的语言），再由机器运行机器码，这样执行程序的效率比较高。像C和C++就是典型的编译型语言。

- **解释型**

  其实解释型语言是相对编译型语言存在的，解释型语言是在运行的时候才进行编译，每次运行都需要编译，这样效率比较低。像JavaScript，Python就是典型的解释型语言

- **解释型语言和编译型语言的区别**

  简单的举个例子：同样一本英文书，找人翻译成中文版的书然后拿给你看就是编译，找一个翻译员在你旁边给你解读书的含义就是解释。两者各有利弊，编译型语言执行效率高，翻译一次可以多次运行。解释性语言执行效率低，每次运行都需要重新翻译。但是解释型的跨平台性相对要好，比如解释给一个懂中文和解释给一个懂日文的人就叫做兼容性。

- **Java的运行机制**

  Java属于两者都有，既有编译过程，又是解释型语言

  java会先执行编译得到 .class 字节码文件，输出到 JVM 虚拟机的类装载器 => 字节码校验器 => 解释器 => 操作系统平台执行

![image-20210311164044599](01-Java%E5%85%A5%E9%97%A8%E5%8F%8A%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA.assets/image-20210311164044599.png)

![image-20210312125734077](01-Java%E5%85%A5%E9%97%A8%E5%8F%8A%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA.assets/image-20210312125734077.png)

![image-20210312125824256](01-Java%E5%85%A5%E9%97%A8%E5%8F%8A%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA.assets/image-20210312125824256.png)

