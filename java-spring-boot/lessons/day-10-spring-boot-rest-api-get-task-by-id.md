# Day 10｜GET 路径参数与 JSON

> 原课程日期：2026-10-20  
> 学习时间：约 10 分钟  
> 连续项目：Task 任务管理系统。课程日期与 Git 实际提交时间分别记录。

## 核心知识（2 分钟）
Express 中 `req.params.id` 对应 Spring MVC 的 `@PathVariable`。在 `@RestController` 中返回 Java 对象，通常由 JSON 消息转换器序列化为响应体。

## 可运行示例（4 分钟）
沿用 Day 09 Spring Boot 项目，添加以下文件。

`model/Task.java`：
```java
package com.example.task.model;
public record Task(int id, String title, boolean completed) {}
```
`service/TaskService.java`：
```java
package com.example.task.service;
import com.example.task.model.Task;
import org.springframework.stereotype.Service;
import org.springframework.http.HttpStatus;
import org.springframework.web.server.ResponseStatusException;
@Service
public class TaskService {
    public Task findById(int id) {
        if (id == 1) return new Task(1, "开发登录接口", false);
        throw new ResponseStatusException(HttpStatus.NOT_FOUND, "任务不存在");
    }
}
```
`controller/TaskController.java`：
```java
package com.example.task.controller;
import com.example.task.model.Task;
import com.example.task.service.TaskService;
import org.springframework.web.bind.annotation.*;
@RestController
@RequestMapping("/api/tasks")
public class TaskController {
    private final TaskService service;
    public TaskController(TaskService service) { this.service = service; }
    @GetMapping("/{id}")
    public Task getTask(@PathVariable int id) {
        return service.findById(id);
    }
}
```
运行 `mvn spring-boot:run`，再执行 `curl http://localhost:8080/api/tasks/1`，预期返回 `{"id":1,"title":"开发登录接口","completed":false}`。

## 实践题（2 分钟）
新增 `GET /api/tasks/{id}/completed` 返回 JSON 布尔值。

## 参考答案与解析（2 分钟）
```java
@GetMapping("/{id}/completed")
public boolean isCompleted(@PathVariable int id) {
    return service.findById(id).completed();
}
```
找不到任务时应返回 404，而不是误报成功。下一课深入依赖注入。
