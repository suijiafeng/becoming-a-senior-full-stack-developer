# Day 01｜认识 JDK、java 与 javac：运行第一个 Java 程序（约 10 分钟）

> 学习路径：Java 基础 → Spring Boot → REST API → 依赖注入 → PostgreSQL → 事务 → 测试 → 部署  
> 连续项目：任务管理系统。今天先让程序运行，下一节建立 Task 类。

## 今日目标（1 分钟）

理解 JDK、JVM、`javac`、`java` 各自负责什么，并在终端运行第一段 Java 代码。建议安装一个受支持的 JDK LTS 版本（例如 JDK 21），确认终端可用：

```bash
java -version
javac -version
```

如果命令无法识别，先检查 JDK 安装及 PATH 环境变量。

## 核心知识（2 分钟）

- **JDK**：开发工具包，包含编译器 `javac` 和运行 Java 程序所需工具。
- **JVM**：Java 虚拟机，负责执行 Java 字节码。
- **javac**：把 `.java` 源文件编译成 `.class` 字节码。
- **java**：启动 JVM 运行编译好的程序。

与 JavaScript 对照：平时可用 `node app.js` 直接运行 JavaScript；入门 Java 的经典流程是 `Main.java → javac → Main.class → java Main`。现代 Java 也支持直接用 `java Main.java` 运行单文件源代码，但本节刻意练习编译流程。

## 可运行示例（3 分钟）

新建文件 **Main.java**，注意文件名与 `public class Main` 一致：

```java
public class Main {
    public static void main(String[] args) {
        String taskTitle = "学习 Java";
        boolean completed = false;

        System.out.println("任务：" + taskTitle);
        System.out.println("已完成：" + completed);
    }
}
```

在文件所在目录执行：

```bash
javac Main.java
java Main
```

预期输出：

```text
任务：学习 Java
已完成：false
```

这里 `String` 表示字符串，`boolean` 表示布尔值；与 JavaScript 的 `let taskTitle = "..."` 不同，Java 在声明变量时明确写出类型。`main` 是此示例的程序入口；`System.out.println` 类似于 JavaScript 的 `console.log`。

## 实践题（2 分钟）

给程序增加两个变量：

1. `int priority = 2;`，表示任务优先级。
2. `String owner = "自己";`，表示负责人。

将它们打印出来，要求输出新增两行：

```text
优先级：2
负责人：自己
```

先自己修改、编译并运行，再核对答案。

## 参考答案与解析（2 分钟）

在 `main` 方法内、已有输出语句后加入：

```java
int priority = 2;
String owner = "自己";
System.out.println("优先级：" + priority);
System.out.println("负责人：" + owner);
```

`int` 是整数基本类型，`String` 是引用类型。Java 的静态类型检查能在编译时发现很多类型不匹配的问题，例如 `int priority = "高";` 会编译失败。

## 面试常见问题

**问：JDK、JRE 和 JVM 有什么区别？**  
答：JVM 执行字节码；JRE 是运行 Java 程序所需的环境概念；JDK 在运行能力之外提供编译、调试等开发工具。现代 JDK 的发行与部署方式不一定单独提供传统的 JRE 安装包。

**问：为什么执行 `java Main` 而不是 `java Main.class`？**  
答：这里传入的是类名，不是文件名。JVM 会在类路径中寻找对应的字节码类。

## 今日验收

- [ ] `java -version` 和 `javac -version` 正常输出版本
- [ ] 可以独立编译并运行 `Main.java`
- [ ] 能解释 `javac` 和 `java` 的区别
- [ ] 完成优先级和负责人的打印练习

## 下一节

**Day 02：Java 类、对象与构造方法。** 把今天散落在 `main` 中的任务字段封装进 `Task` 类，开始搭建真正的任务管理业务模型。
