# Day 07｜package 与项目目录结构

> 原课程日期：2026-10-17  
> 学习时间：约 10 分钟  
> 项目：Task 任务管理系统。课程日期与 Git 实际提交时间分别记录。

## 核心知识（2 分钟）
Java 的 `package` 声明类型所属包，`import` 引用其他包的类型；与 JavaScript 相对路径 import 不同。公开顶级类通常独立放在同名 .java 文件中。

## 可运行示例（4 分钟）
目录：
```text
src/com/example/task/Main.java
src/com/example/task/model/Task.java
src/com/example/task/util/TaskPrinter.java
```
Task.java：
```java
package com.example.task.model;
public class Task {
    private final int id;
    private final String title;
    public Task(int id, String title) { this.id=id; this.title=title; }
    public int getId() { return id; }
    public String getTitle() { return title; }
}
```
TaskPrinter.java：
```java
package com.example.task.util;
import com.example.task.model.Task;
public class TaskPrinter {
    public void print(Task task) {
        System.out.println("任务 #" + task.getId() + "：" + task.getTitle());
    }
}
```
Main.java：
```java
package com.example.task;
import com.example.task.model.Task;
import com.example.task.util.TaskPrinter;
public class Main {
    public static void main(String[] args) {
        new TaskPrinter().print(new Task(1, "开发登录接口"));
    }
}
```
编译运行：
```bash
javac -encoding UTF-8 -d out src/com/example/task/model/Task.java src/com/example/task/util/TaskPrinter.java src/com/example/task/Main.java
java -cp out com.example.task.Main
```

## 实践题（2 分钟）
为什么运行时要写 `com.example.task.Main`，而不是仅写 `Main`？

## 参考答案与解析（2 分钟）
因为 Main 属于 `com.example.task` 包，运行时要指定完全限定类名。下一课用 Maven 规范化编译和依赖管理。
