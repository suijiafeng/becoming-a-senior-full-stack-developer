# Day 06｜异常处理与业务错误

> 原课程日期：2026-10-16  
> 学习时间：约 10 分钟  
> 项目：Task 任务管理系统。课程日期与 Git 实际提交时间分别记录。

## 核心知识（2 分钟）
Java 的 `throw`、`try/catch` 类似 JavaScript；`RuntimeException` 是非受检异常。业务对象不存在时，返回 null 容易造成后续空指针，显式抛出业务异常更清晰。

## 可运行示例（4 分钟）
保存为 Main.java：
```java
import java.util.Map;
public class Main {
    public static void main(String[] args) {
        TaskService service = new TaskService();
        try {
            System.out.println(service.findById(99));
        } catch (TaskNotFoundException e) {
            System.out.println("错误：" + e.getMessage());
        }
    }
}
class TaskNotFoundException extends RuntimeException {
    TaskNotFoundException(int id) { super("任务不存在：" + id); }
}
class TaskService {
    private final Map<Integer, String> tasks = Map.of(1, "开发登录接口");
    String findById(int id) {
        String task = tasks.get(id);
        if (task == null) throw new TaskNotFoundException(id);
        return task;
    }
}
```
运行：`javac Main.java && java Main`；输出 `错误：任务不存在：99`。

## 实践题（2 分钟）
新增 `reopenTask(int id)`：任务不存在时抛出 TaskNotFoundException，存在时恢复未完成状态。你会把异常放在 Controller 还是 Service？

## 参考答案与解析（2 分钟）
应在 Service 识别业务异常；Controller 或统一异常处理器将其转换为 HTTP 404。示意：
```java
Task task = findById(id); // 不存在时抛异常
task.reopen();             // Task 内部设置 completed=false
```
面试点：异常用于表达错误路径，不应将所有正常分支都用异常处理。下一课学习 package 和目录结构。
