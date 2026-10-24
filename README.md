# Becoming a Senior Full-Stack Developer

> 从前端工程经验出发，系统学习 Java、Spring Boot、数据库、工程化与 AI 应用开发。
>
> **使用方式：选择学习阶段 → 点击课程 → 阅读知识点 → 运行代码 → 完成练习。**

## 快速开始

| 学习入口 | 适合谁 | 资料 |
|---|---|---|
| Java 基础 | 已会 JavaScript、刚开始学 Java | [第 01～08 课](#第一阶段java-基础day-0108) |
| Spring Boot | 想写自己的后端 API | [第 09～14 课](#第二阶段spring-boot-与-rest-apiday-0914) |
| 前端复习 | 想巩固原有前端技能 | [5 个前端 Demo](#前端实践资料) |
| 后续规划 | 想继续学数据库、测试和部署 | [学习路线](#后续学习路线待完成) |

**当前进度：**已整理并提交 Day 01～14 的课程文档；Task 系统目前以分阶段教学代码为主，**尚未声称完成数据库持久化或生产部署**。

## 第一阶段：Java 基础（Day 01～08）

| 课次 | 点击学习资料 | 重点 |
|---|---|---|
| 01 | [Java 运行环境、javac](java-spring-boot/lessons/day-01-java-jdk-javac-and-first-program.md) | JDK、JVM、编译运行 |
| 02 | [类与对象](java-spring-boot/lessons/day-02-java-classes-and-objects.md) | 类、对象、构造方法 |
| 03 | [类型与字符串比较](java-spring-boot/lessons/day-03-java-types-string-equals.md) | 基本类型、String、equals |
| 04 | [集合与任务列表](java-spring-boot/lessons/day-04-java-list-arraylist-task-manager.md) | List、ArrayList、泛型 |
| 05 | [封装与业务逻辑](java-spring-boot/lessons/day-05-java-encapsulation-task-service.md) | private、Service |
| 06 | [异常处理](java-spring-boot/lessons/day-06-java-exceptions-and-business-errors.md) | throw、try/catch |
| 07 | [包与项目结构](java-spring-boot/lessons/day-07-java-packages-and-project-structure.md) | package、import |
| 08 | [Maven 构建](java-spring-boot/lessons/day-08-maven-project-and-dependency-management.md) | pom.xml、构建生命周期 |

## 第二阶段：Spring Boot 与 REST API（Day 09～14）

| 课次 | 点击学习资料 | 重点 |
|---|---|---|
| 09 | [第一个 HTTP 服务](java-spring-boot/lessons/day-09-spring-boot-first-http-service.md) | @SpringBootApplication、@GetMapping |
| 10 | [GET 与 JSON](java-spring-boot/lessons/day-10-spring-boot-rest-api-get-task-by-id.md) | @PathVariable、JSON |
| 11 | [依赖注入](java-spring-boot/lessons/day-11-spring-boot-dependency-injection.md) | IoC、Bean、@Service |
| 12 | [创建任务接口](java-spring-boot/lessons/day-12-spring-boot-post-request-body-dto.md) | POST、DTO、@RequestBody |
| 13 | [请求参数校验](java-spring-boot/lessons/day-13-spring-boot-bean-validation.md) | @Valid、@NotBlank |
| 14 | [更新任务状态](java-spring-boot/lessons/day-14-spring-boot-patch-task-status-and-idempotency.md) | PATCH、幂等性 |

**完整文件目录：** [java-spring-boot/lessons](java-spring-boot/lessons/)

### 建议的每日 10 分钟学习法

- **2 分钟**：阅读核心知识，联系 JavaScript 已有经验。
- **4 分钟**：运行 Java / Spring Boot 示例，观察输出。
- **3 分钟**：独立完成练习，不先看参考答案。
- **1 分钟**：对照解析，记录一个面试知识点。

> 课程是逐日演进的学习材料，不一定能将不同日期的代码直接拼接成一个项目。建议按每课说明单独练习，后续再整合为统一的 Task 后端工程。

## Task 任务管理系统：贯穿课程的实践项目

目标是逐步实现以下功能，而非仅记忆语法：

| 功能 | 学习资料 | 说明 |
|---|---|---|
| 创建 Task 对象 | [Day 02](java-spring-boot/lessons/day-02-java-classes-and-objects.md) | Java 对象建模 |
| 任务筛选与列表 | [Day 04](java-spring-boot/lessons/day-04-java-list-arraylist-task-manager.md) | 内存集合 |
| 根据 ID 查找及完成任务 | [Day 05](java-spring-boot/lessons/day-05-java-encapsulation-task-service.md) | Service 业务逻辑 |
| 业务异常处理 | [Day 06](java-spring-boot/lessons/day-06-java-exceptions-and-business-errors.md) | 失败路径 |
| 启动 HTTP 服务 | [Day 09](java-spring-boot/lessons/day-09-spring-boot-first-http-service.md) | Spring Boot |
| 查询任务 JSON | [Day 10](java-spring-boot/lessons/day-10-spring-boot-rest-api-get-task-by-id.md) | GET |
| 接收创建请求 | [Day 12](java-spring-boot/lessons/day-12-spring-boot-post-request-body-dto.md) | POST |
| 校验请求数据 | [Day 13](java-spring-boot/lessons/day-13-spring-boot-bean-validation.md) | DTO 校验 |
| 修改任务状态 | [Day 14](java-spring-boot/lessons/day-14-spring-boot-patch-task-status-and-idempotency.md) | PATCH |

## 前端实践资料

保留仓库原有的前端学习项目，作为从前端向全栈转型的能力基础。点击名称可直接打开入口文件。

| 项目 | 学习资料 | 主要练习内容 |
|---|---|---|
| demo1 | [高级待办事项列表](demo1/index.html) | 语义化 HTML、DOM 交互、Web Components、响应式布局 |
| demo2 | [高级图片库](demo2/index.html) | CSS Grid、Intersection Observer、懒加载 |
| demo3 | [智能家居控制面板](demo3/index.html) | 模块化、主题、状态管理、图表、拖拽 |
| demo4 | [高级图表仪表板](demo4/index.html) | Chart.js、数据筛选、可视化、响应式设计 |
| demo5 | [卡片式在线编辑器](demo5/index.html) | CodeMirror、Prettier、实时预览、LocalStorage |

### 如何运行前端 Demo

克隆仓库后进入相应 Demo 目录，通过本地静态服务器访问，例如：

```bash
git clone https://github.com/suijiafeng/becoming-a-senior-full-stack-developer.git
cd becoming-a-senior-full-stack-developer/demo1
python3 -m http.server 8000
```

打开 `http://localhost:8000`。部分 Demo 可能依赖 CDN、浏览器 API 或其他环境配置，请以项目实际代码为准。

## 后续学习路线（待完成）

以下是计划，不是已经发布的课程。新课提交后再补充真实链接。

| 阶段 | 待学习主题 | 对应实践目标 |
|---|---|---|
| 数据持久化 | PostgreSQL、SQL、Spring Data JPA | 将任务从内存保存到数据库 |
| 业务可靠性 | 事务、异常处理、并发基础 | 确保任务状态一致 |
| 质量保障 | JUnit、Mockito、HTTP 接口测试 | 自动验证业务逻辑 |
| 工程交付 | 配置管理、Docker、部署 | 将后端服务部署上线 |
| 全栈联调 | Vue / React 调用 Task API | 完成可交互任务管理系统 |
| AI 应用扩展 | 模型 API、RAG、检索与评测 | 探索 Java 后端与 AI 应用结合 |

## 学习资料补充

除仓库内课程外，遇到概念不清晰时可查阅官方文档：

| 资料 | 用途 |
|---|---|
| [Java 官方学习资料](https://dev.java/learn/) | Java 语言基础与进阶 |
| [Maven 官方指南](https://maven.apache.org/guides/) | pom.xml 与构建 |
| [Spring Boot 官方文档](https://docs.spring.io/spring-boot/index.html) | Spring Boot 配置与启动 |
| [Spring Framework 官方文档](https://docs.spring.io/spring-framework/reference/) | IoC、DI、Spring MVC |
| [PostgreSQL 官方文档](https://www.postgresql.org/docs/) | SQL、数据库基础 |
| [JUnit 5 用户指南](https://junit.org/junit5/docs/current/user-guide/) | Java 自动化测试 |
| [MDN JavaScript](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript) | 与 Java 进行概念对比 |

## 说明

本仓库用于个人学习、知识整理和工程实践。课程日期记录原始学习顺序，Git Commit 日期记录真实提交时间。示例以教学为目的，部署生产环境前仍需补充鉴权、安全、测试、持久化和运维能力。
