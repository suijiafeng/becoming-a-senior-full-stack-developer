# Day 03｜Java 类型与 String.equals

> 原课程日期：2026-10-13  
> 学习时间：约 10 分钟  
> 项目：Task 任务管理系统。课程日期与 Git 实际提交时间分别记录。

## 核心知识（2 分钟）
Java 是静态类型语言，`int`、`boolean` 是基本类型，`String` 是引用类型。与 JavaScript 的 `===` 不同，Java 中字符串内容比较通常用 `equals()`。

```java
String status = "OPEN";
int priority = 3;
boolean completed = false;
System.out.println("OPEN".equals(status));
```

`"OPEN".equals(status)` 还可以避免 status 为 null 时调用方法造成的空指针异常。

## 可运行示例（4 分钟）
保存为 Main.java：
```java
public class Main {
    public static void main(String[] args) {
        Task task = new Task("开发登录接口", 3, false, "OPEN");
        System.out.println(task.shouldHandle());
    }
}
class Task {
    String title;
    int priority;
    boolean completed;
    String status;
    Task(String title, int priority, boolean completed, String status) {
        this.title = title;
        this.priority = priority;
        this.completed = completed;
        this.status = status;
    }
    boolean isOpen() { return "OPEN".equals(status); }
    boolean shouldHandle() { return isOpen() && !completed && priority >= 3; }
}
```
运行：`javac Main.java && java Main`；预期输出 `true`。

## 实践题（2 分钟）
修改任务状态为 DONE，再判断 `shouldHandle()` 应返回什么？为什么？

## 参考答案与解析（2 分钟）
```java
Task task = new Task("开发登录接口", 3, false, "DONE");
System.out.println(task.shouldHandle()); // false
```
因为 `isOpen()` 为 false，`&&` 短路后不再继续求值。面试追问：`==` 对引用类型比较对象身份，`String.equals` 比较内容。下一课使用 List 管理多个 Task。
