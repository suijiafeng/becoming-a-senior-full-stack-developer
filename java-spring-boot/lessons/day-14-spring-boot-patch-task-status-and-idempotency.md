# Day 14｜Spring Boot PATCH 更新任务状态与幂等性

学习时间：约 10 分钟。延续 Task 任务管理系统，第 13 课完成参数校验，本课实现任务状态更新。

## 核心知识（2 分钟）

- `PUT` 通常表示替换资源，按 HTTP 语义具有幂等性。
- `PATCH` 表示部分更新，不保证幂等；将 `completed` 固定设置为 `true` 或 `false` 是幂等的。
- JavaScript 中 `task.completed = true` 是幂等赋值，`task.count++` 则不是。

## 可运行示例（5 分钟）

沿用已有 Spring Boot Web 和 Validation 项目。下面代码放在对应类中。

`UpdateTaskStatusRequest.java`：

```java
package com.example.task.dto;

import jakarta.validation.constraints.NotNull;

public record UpdateTaskStatusRequest(@NotNull Boolean completed) {}
```

`TaskController.java` 增加方法（已有构造器注入的 `TaskService service`）：

```java
@PatchMapping("/{id}")
public Task updateStatus(@PathVariable int id,
                         @Valid @RequestBody UpdateTaskStatusRequest body) {
    return service.setCompleted(id, body.completed());
}
```

`TaskService.java` 增加方法（沿用之前的 `List<Task> tasks` 和 `findById`）：

```java
public Task setCompleted(int id, boolean completed) {
    Task task = findById(id);
    if (completed) {
        task.complete();
    } else {
        task.reopen();
    }
    return task;
}
```

`Task.java` 中增加：

```java
public void reopen() {
    this.completed = false;
}
```

确保 Controller 已导入 `@PatchMapping`、`@PathVariable`、`@RequestBody`、`@Valid` 和 DTO 类型。启动：

```bash
mvn spring-boot:run
curl -i -X PATCH http://localhost:8080/api/tasks/1 -H 'Content-Type: application/json' -d '{"completed":true}'
```

## 实践题（2 分钟）

将任务 1 的状态恢复为未完成，并验证重复发送同一请求时状态是否变化。

## 参考答案与解析（1 分钟）

```bash
curl -i -X PATCH http://localhost:8080/api/tasks/1 -H 'Content-Type: application/json' -d '{"completed":false}'
curl http://localhost:8080/api/tasks/1
```

预期 JSON 中 `completed` 为 `false`。重复请求不会继续改变最终状态，因此这一 PATCH 操作是幂等的。若使用 `count++` 则通常不幂等。

**面试题：PATCH 一定不幂等吗？** 不是，取决于操作的具体语义。

下一课：Spring Data JPA 与 Repository，为 PostgreSQL 持久化做准备。
