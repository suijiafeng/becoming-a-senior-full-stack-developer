# Day 13｜@Valid 与 @NotBlank 参数校验

> 原课程日期：2026-10-23  
> 学习时间：约 10 分钟  
> 连续项目：Task 任务管理系统。课程日期与 Git 实际提交时间分别记录。

## 核心知识（2 分钟）
Day 12 在 Service 中手写空标题判断；今天使用 Bean Validation 让 DTO 声明约束。Spring Boot 项目需添加 `spring-boot-starter-validation` 依赖（使用项目现有的 Spring Boot 依赖管理）。

## 可运行示例（4 分钟）
在 `pom.xml` 的 dependencies 下添加：
```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-validation</artifactId>
</dependency>
```
将 Day 12 的 CreateTaskRequest 修改为：
```java
package com.example.task.dto;
import jakarta.validation.constraints.NotBlank;
import jakarta.validation.constraints.Size;
public record CreateTaskRequest(
    @NotBlank(message = "任务标题不能为空")
    @Size(max = 40, message = "任务标题不能超过40个字符")
    String title
) {}
```
Controller 创建方法的参数修改为：
```java
public ResponseEntity<Task> create(@Valid @RequestBody CreateTaskRequest body)
```
并导入 `jakarta.validation.Valid`。Spring MVC 在调用方法体前校验 DTO，失败时默认返回 HTTP 400。测试：
```bash
curl -i -X POST http://localhost:8080/api/tasks -H 'Content-Type: application/json' -d '{"title":"   "}'
```
预期 HTTP 400。若需固定 JSON 错误结构，可使用 `@RestControllerAdvice` 捕获 `MethodArgumentNotValidException`。

## 实践题（2 分钟）
限制标题最多 40 字符，并比较 `@NotNull`、`@NotEmpty`、`@NotBlank`。

## 参考答案与解析（2 分钟）
上面的 `@Size(max=40)` 即为参考答案。`@NotNull` 只排除 null；`@NotEmpty` 还排除空字符串或集合；`@NotBlank` 针对字符串，还排除纯空白。下一课使用 PATCH 更新任务状态。
