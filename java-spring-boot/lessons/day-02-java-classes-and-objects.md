# Day 02｜Java 类、对象与构造方法（10 分钟）

> 学习路径：Java 基础 → Spring Boot → REST API → 依赖注入 → PostgreSQL → 事务 → 测试 → 部署  
> 连续实战：从内存版任务管理器逐步升级为可部署的全栈任务管理系统。  
> 前置知识：上一节已接触 `java` 和 `javac`，本节学习如何组织业务数据。

## 今日目标（1 分钟）
理解 **类（class）** 是模板、**对象（object）** 是实例、**构造方法（constructor）** 负责初始化对象。今天实现第一个任务实体 `Task`。

## JavaScript 对照（2 分钟）

JavaScript 可以这样写：

```js
class Task {
  constructor(title) {
    this.title = title;
    this.completed = false;
  }
}
const task = new Task("学习 Java");
console.log(task.title);
```

Java 也使用 `class` 和 `new`，但需要声明字段类型；构造方法与类同名，没有返回值类型。

## 可运行的 Java 示例（3 分钟）

将下面代码保存为 **Main.java**：

```java
class Task {
    private String title;
    private boolean completed;

    public Task(String title) {
        this.title = title;
        this.completed = false;
    }

    public void complete() {
        this.completed = true;
    }

    public String getTitle() {
        return title;
    }

    public boolean isCompleted() {
        return completed;
    }
}

public class Main {
    public static void main(String[] args) {
        Task task = new Task("学习 Java");
        System.out.println(task.getTitle() + ": " + task.isCompleted());
        task.complete();
        System.out.println(task.getTitle() + ": " + task.isCompleted());
    }
}
```

运行：

```bash
javac Main.java
java Main
```

预期输出：

```text
学习 Java: false
学习 Java: true
```

理解要点：`private` 限制外部直接修改字段；`public` 方法提供明确的访问入口；`this.title` 表示当前对象的字段；`boolean` 是 Java 的布尔基本类型。一个 `Main.java` 文件可以包含多个非 `public` 顶层类，但此例只有 `Main` 是 `public`。

## 实践题（2 分钟）

给 `Task` 增加一个 `priority`（优先级，整数）字段：
1. 创建任务时通过构造方法传入优先级。
2. 增加 `getPriority()`。
3. 在 `main` 中创建优先级为 2 的任务并打印优先级。

先独立完成，再看答案。

## 参考答案与解析（2 分钟）

在 `Task` 中增加字段，并把构造方法改成：

```java
private int priority;

public Task(String title, int priority) {
    this.title = title;
    this.completed = false;
    this.priority = priority;
}

public int getPriority() {
    return priority;
}
```

在 `main` 中改为：

```java
Task task = new Task("学习 Java", 2);
System.out.println("优先级: " + task.getPriority());
task.complete();
System.out.println(task.getTitle() + ": " + task.isCompleted());
```

注意：改了构造方法参数后，原来的 `new Task("学习 Java")` 将不再匹配，需要同步修改调用处。Java 会在编译阶段检查参数数量和类型。

## 面试常见问题

**问：构造方法和普通方法有什么区别？**  
答：构造方法在 `new` 对象时执行，名称必须与类名相同且没有返回值类型；普通方法用于执行对象行为，可以有返回值类型。

**问：为什么字段建议使用 `private`？**  
答：避免外部任意改动内部状态，便于在方法中集中验证规则。这是封装的基础。

## 今日验收

- [ ] 能用 `javac Main.java && java Main` 运行示例（Windows PowerShell 可分两条执行）
- [ ] 能解释 `class`、`new`、`this`、`private`
- [ ] 能独立为 `Task` 增加字段、构造参数和 getter

## 下一节预告

**Day 03：方法、参数与返回值**。为任务增加 `rename(String newTitle)`，验证标题不能为空，为未来的 REST API 业务逻辑做准备。

> 学习原则：每节约 10 分钟，一个核心知识点、一段可运行代码、一题实战及答案；后续始终围绕同一个任务管理项目递进。
