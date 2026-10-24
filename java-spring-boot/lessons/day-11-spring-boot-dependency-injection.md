# Day 11｜IoC、Bean 与构造器注入

> 原课程日期：2026-10-21  
> 学习时间：约 10 分钟  
> 连续项目：Task 任务管理系统。课程日期与 Git 实际提交时间分别记录。

## 核心知识（2 分钟）
IoC：对象的创建和组装交给 Spring 容器；DI：容器向对象提供其依赖；Bean：容器管理的对象。JavaScript 中 `new Controller(new Service())` 需要手工组装，Spring 可通过构造器自动注入。

## 可运行示例（4 分钟）
沿用 Day 10 的 TaskApplication、Task、TaskService 和 TaskController。注意 `TaskService` 已使用 `@Service`，`TaskController` 使用构造器：
```java
private final TaskService service;
public TaskController(TaskService service) {
    this.service = service;
}
```
只有一个构造器时，通常不必标注 `@Autowired`。不要在 Controller 内 `new TaskService()`，否则绕过 Spring 容器的生命周期管理。

## 实践题（2 分钟）
新增统计接口 `GET /api/tasks/count`，要求通过构造器注入同一个 TaskService。为便于演示，先返回固定种子数据的数量 1。

## 参考答案与解析（2 分钟）
`TaskService` 增加：
```java
public int countTasks() { return 1; }
```
`controller/TaskStatsController.java`：
```java
package com.example.task.controller;
import com.example.task.service.TaskService;
import org.springframework.web.bind.annotation.*;
@RestController
@RequestMapping("/api/tasks")
public class TaskStatsController {
    private final TaskService service;
    public TaskStatsController(TaskService service) { this.service = service; }
    @GetMapping("/count")
    public int count() { return service.countTasks(); }
}
```
Spring Bean 默认 singleton 作用域，同一个容器中的多个 Controller 可以共享同一个 Service Bean。固定数量仅用于本节演示，后续会换成实际集合和数据库。下一课接收 POST JSON。
