# Day 04｜List、ArrayList 与任务列表

> 原课程日期：2026-10-14  
> 学习时间：约 10 分钟  
> 项目：Task 任务管理系统。课程日期与 Git 实际提交时间分别记录。

## 核心知识（2 分钟）
JavaScript 的 `tasks.push(x)` 对应 Java 的 `tasks.add(x)`，`tasks.length` 对应 `tasks.size()`。声明 `List<Task> tasks = new ArrayList<>()` 是面向接口编程，泛型限制元素类型。

## 可运行示例（4 分钟）
保存为 Main.java：
```java
import java.util.ArrayList;
import java.util.List;
public class Main {
    public static void main(String[] args) {
        TaskManager manager = new TaskManager();
        manager.addTask(new Task("开发登录接口", 3, false, "OPEN"));
        manager.addTask(new Task("编写文档", 1, false, "OPEN"));
        for (Task task : manager.getPendingTasks()) {
            System.out.println(task.title);
        }
    }
}
class Task {
    String title; int priority; boolean completed; String status;
    Task(String title, int priority, boolean completed, String status) {
        this.title=title; this.priority=priority;
        this.completed=completed; this.status=status;
    }
    boolean shouldHandle() {
        return "OPEN".equals(status) && !completed && priority >= 3;
    }
}
class TaskManager {
    private final List<Task> tasks = new ArrayList<>();
    void addTask(Task task) { tasks.add(task); }
    List<Task> getAllTasks() { return new ArrayList<>(tasks); }
    List<Task> getPendingTasks() {
        List<Task> result = new ArrayList<>();
        for (Task task : tasks) {
            if (task.shouldHandle()) result.add(task);
        }
        return result;
    }
}
```
运行：`javac Main.java && java Main`，输出 `开发登录接口`。

## 实践题（2 分钟）
添加一个优先级为 4、状态为 DONE 的任务，它会进入待处理列表吗？

## 参考答案（2 分钟）
不会，因为 `"OPEN".equals(status)` 为 false。Java 的增强 for 循环与 JavaScript `for...of` 类似；`getAllTasks()` 返回新列表可防止调用者直接修改内部列表结构，但仍是浅拷贝。下一课引入封装和 Service。
