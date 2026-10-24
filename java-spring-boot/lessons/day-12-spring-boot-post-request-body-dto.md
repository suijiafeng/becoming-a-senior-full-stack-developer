# Day 12｜POST、@RequestBody 与 DTO

> 原课程日期：2026-10-22  
> 学习时间：约 10 分钟  
> 连续项目：Task 任务管理系统。课程日期与 Git 实际提交时间分别记录。

## 核心知识（2 分钟）
前端 `fetch('/api/tasks',{method:'POST',headers:{'Content-Type':'application/json'},body:JSON.stringify({title:'学习 Spring Boot'})})`；Spring MVC 用 `@PostMapping` 和 `@RequestBody` 接收 JSON。DTO 用于承载请求数据，避免直接暴露实体对象。

## 可运行示例（4 分钟）
沿用 Day 11 Spring Boot 项目，将 TaskService 替换为可创建任务的内存版本：
```java
package com.example.task.service;
import com.example.task.model.Task;
import org.springframework.stereotype.Service;
import org.springframework.web.server.ResponseStatusException;
import org.springframework.http.HttpStatus;
import java.util.concurrent.ConcurrentHashMap;
import java.util.concurrent.atomic.AtomicInteger;
@Service
public class TaskService {
    private final ConcurrentHashMap<Integer, Task> tasks = new ConcurrentHashMap<>();
    private final AtomicInteger nextId = new AtomicInteger(2);
    public TaskService() { tasks.put(1, new Task(1,"开发登录接口",false)); }
    public Task findById(int id) {
        Task t = tasks.get(id);
        if (t == null) throw new ResponseStatusException(HttpStatus.NOT_FOUND);
        return t;
    }
    public int countTasks() { return tasks.size(); }
    public Task createTask(String title) {
        if (title == null || title.isBlank())
            throw new ResponseStatusException(HttpStatus.BAD_REQUEST, "任务标题不能为空");
        Task task = new Task(nextId.getAndIncrement(), title.strip(), false);
        tasks.put(task.id(), task);
        return task;
    }
}
```
新增 DTO：
```java
package com.example.task.dto;
public record CreateTaskRequest(String title) {}
```
在 TaskController 中添加：
```java
@PostMapping
public ResponseEntity<Task> create(@RequestBody CreateTaskRequest body) {
    Task task = service.createTask(body.title());
    return ResponseEntity.created(URI.create("/api/tasks/" + task.id())).body(task);
}
```
并导入 `java.net.URI`、`org.springframework.http.ResponseEntity` 和 DTO。执行：
```bash
curl -i -X POST http://localhost:8080/api/tasks -H 'Content-Type: application/json' -d '{"title":"学习 Spring Boot"}'
```
预期 HTTP 201，响应体包含新任务 ID、标题和 completed=false。

## 实践题（2 分钟）
空标题或全空格标题应该返回什么状态码？

## 参考答案与解析（2 分钟）
返回 HTTP 400；使用 `title == null || title.isBlank()` 校验。下一课改为 Bean Validation 声明式校验。
