# Day 9｜第一个 Spring Boot HTTP 服务

> 原课程日期：2026-10-19  
> 学习时间：约 10 分钟  
> 连续项目：Task 任务管理系统。课程日期与 Git 实际提交时间分别记录。

## 核心知识（2 分钟）
Express 的 `app.get('/api/hello', handler)` 对应 Spring MVC 的 `@GetMapping("/api/hello")`。`@SpringBootApplication` 组合自动配置与组件扫描；`@RestController` 用于返回 HTTP 响应体。

## 可运行示例（4 分钟）
在 Spring Boot 4.x 项目的 `pom.xml` 中引入 `spring-boot-starter-webmvc`，并使用 Spring Boot parent 管理依赖版本；如果使用 Spring Boot 3.x 则改为 `spring-boot-starter-web`。下方 Java 代码对这两种版本均适用。

`src/main/java/com/example/task/TaskApplication.java`：
```java
package com.example.task;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
@SpringBootApplication
public class TaskApplication {
    public static void main(String[] args) {
        SpringApplication.run(TaskApplication.class, args);
    }
}
```
`src/main/java/com/example/task/controller/HelloController.java`：
```java
package com.example.task.controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;
@RestController
public class HelloController {
    @GetMapping("/api/hello")
    public String hello() { return "Task API is running"; }
}
```
启动：`mvn spring-boot:run`；验证：`curl http://localhost:8080/api/hello`，预期输出 `Task API is running`。

## 实践题（2 分钟）
增加 `GET /api/tasks/status`，返回 `Task service: ready`。

## 参考答案与解析（2 分钟）
```java
@GetMapping("/api/tasks/status")
public String status() { return "Task service: ready"; }
```
这里仅返回固定字符串，并非真正的健康检查。下一课查询任务 JSON。
