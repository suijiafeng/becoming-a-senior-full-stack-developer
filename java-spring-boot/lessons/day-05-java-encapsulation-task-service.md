# Day 05｜封装与 TaskService

> 原课程日期：2026-10-15  
> 学习时间：约 10 分钟  
> 项目：Task 任务管理系统。课程日期与 Git 实际提交时间分别记录。

## 核心知识（2 分钟）
`private` 限制外部直接修改字段，`public` 暴露有业务意义的方法。与 JavaScript class 类似，但 Java 有编译期访问控制。不要到处写 `task.completed = true`，应调用 `task.complete()`。

## 可运行示例（4 分钟）
保存为 Main.java：
```java
import java.util.ArrayList;
import java.util.List;
public class Main {
    public static void main(String[] args) {
        TaskService service = new TaskService();
        service.addTask(new Task(1, "开发登录接口"));
        System.out.println(service.completeTask(1)); // true
        System.out.println(service.completeTask(1)); // false
    }
}
class Task {
    private final int id;
    private final String title;
    private boolean completed;
    Task(int id, String title) { this.id=id; this.title=title; }
    int getId() { return id; }
    String getTitle() { return title; }
    boolean isCompleted() { return completed; }
    void complete() { completed=true; }
}
class TaskService {
    private final List<Task> tasks = new ArrayList<>();
    void addTask(Task task) { tasks.add(task); }
    Task findById(int id) {
        for (Task task : tasks) if (task.getId()==id) return task;
        return null;
    }
    boolean completeTask(int id) {
        Task task = findById(id);
        if (task == null || task.isCompleted()) return false;
        task.complete();
        return true;
    }
}
```
运行：`javac Main.java && java Main`。

## 实践题（2 分钟）
为什么第二次完成任务返回 false？若 ID=99 又会怎样？

## 参考答案与解析（2 分钟）
第二次因 `isCompleted()` 为 true 返回 false；ID=99 因 `task == null` 返回 false。条件使用 `||` 短路避免空指针。Controller 负责 HTTP，Service 负责业务规则；下一课学习异常。
