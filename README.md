# Becoming a Senior Full-Stack Developer

> 从前端工程能力出发，系统学习 Java / Spring Boot 后端开发，并逐步扩展到数据库、测试、部署和 AI 应用工程。

## 仓库定位

这是一个持续更新的个人工程学习仓库，不是单一可直接部署的产品。仓库保留已有的 HTML、CSS、JavaScript 前端实践，同时新增按天组织的 Java / Spring Boot 学习笔记，目标是逐步具备独立开发、测试和部署小型全栈服务的能力。

学习原则：**每天约 10 分钟，围绕同一个 Task 任务管理系统递进**。每课包含核心知识、Java 与 JavaScript 对比、代码示例、练习、参考答案及面试知识点。课程文档里的原始学习日期不等于 Git 提交日期。

## 当前进度

- Java / Spring Boot 学习文档：**Day 01～Day 14 已整理并提交**。
- 已涉及：Java 基础、集合、封装、异常、包管理、Maven、Spring Boot HTTP、REST API、依赖注入、DTO、参数校验、PATCH 与幂等性。
- **Task API 仍是渐进式教学项目**：课程中的示例按日演进，不代表仓库已经包含一套统一集成、完成数据库持久化并部署的生产级后端。
- 下一阶段：Spring Data JPA、PostgreSQL、事务、测试、部署及前后端联调。

## Java / Spring Boot 课程目录

课程文件位置：[`java-spring-boot/lessons/`](java-spring-boot/lessons/)。

| Day | 课程 | 状态 |
|---|---|---|
| 01 | [JDK、JVM、javac 与第一个程序](java-spring-boot/lessons/day-01-java-jdk-javac-and-first-program.md) | 已整理 |
| 02 | [Java 类与对象](java-spring-boot/lessons/day-02-java-classes-and-objects.md) | 已整理 |
| 03 | [基本类型与 String.equals](java-spring-boot/lessons/day-03-java-types-string-equals.md) | 已整理 |
| 04 | [List、ArrayList 与任务列表](java-spring-boot/lessons/day-04-java-list-arraylist-task-manager.md) | 已整理 |
| 05 | [封装与 TaskService](java-spring-boot/lessons/day-05-java-encapsulation-task-service.md) | 已整理 |
| 06 | [异常处理与业务错误](java-spring-boot/lessons/day-06-java-exceptions-and-business-errors.md) | 已整理 |
| 07 | [package 与项目目录](java-spring-boot/lessons/day-07-java-packages-and-project-structure.md) | 已整理 |
| 08 | [Maven 项目构建](java-spring-boot/lessons/day-08-maven-project-and-dependency-management.md) | 已整理 |
| 09 | [第一个 Spring Boot HTTP 服务](java-spring-boot/lessons/day-09-spring-boot-first-http-service.md) | 已整理 |
| 10 | [REST API、路径参数与 JSON](java-spring-boot/lessons/day-10-spring-boot-rest-api-get-task-by-id.md) | 已整理 |
| 11 | [IoC、Bean 与依赖注入](java-spring-boot/lessons/day-11-spring-boot-dependency-injection.md) | 已整理 |
| 12 | [POST、@RequestBody 与 DTO](java-spring-boot/lessons/day-12-spring-boot-post-request-body-dto.md) | 已整理 |
| 13 | [@Valid 与参数校验](java-spring-boot/lessons/day-13-spring-boot-bean-validation.md) | 已整理 |
| 14 | [PATCH 更新与幂等性](java-spring-boot/lessons/day-14-spring-boot-patch-task-status-and-idempotency.md) | 已整理 |

### Task 项目学习路线

```text
Java 基础 → 集合与封装 → 异常处理 → Maven
         → Spring Boot → REST API → 参数校验
         → 数据库与 JPA → 事务 → 自动化测试
         → 部署 → 前后端联调
```

计划逐步实现：创建任务、按 ID 查询、任务列表、完成/取消完成、输入校验、统一错误处理、PostgreSQL 持久化、接口测试与部署。未完成的部分仅是学习计划，不作为已实现功能展示。

### 如何学习

1. 从 [Day 01](java-spring-boot/lessons/day-01-java-jdk-javac-and-first-program.md) 开始，按顺序阅读课程。
2. 将每节课的示例放在独立练习目录中运行，避免不同课程同名类相互冲突。
3. Java 基础示例使用 JDK；Spring Boot 示例需要匹配课程所用的 Spring Boot、JDK 与 Maven 版本，按课程说明配置依赖。
4. 完成练习题后再对照参考答案，并记录遇到的错误和解决方式。

## 前端工程实践

原有前端 Demo 仍然保留，用于复习浏览器 API、组件化、交互、可视化与工程组织。对于静态页面，可在对应 Demo 目录运行本地静态服务器（例如 `python3 -m http.server 8000`），再通过浏览器访问；部分 Demo 依赖 CDN 或浏览器环境。

### demo1 高级待办事项列表 

入口：`demo1/index.html`（按顶部说明用本地服务器打开）

这个待办事项列表应用展示了更多的HTML、CSS和JavaScript概念:

HTML:

- 使用了语义化的标签如 `<form>` 和 `<ul>`

- 使用了 id 属性来选择特定元素
- Web Components

CSS:

- 使用了更复杂的选择器和样式

- 实现了响应式设计（使用 max-width 和 flex）
- 运用了一些简单的动画效果（如按钮的 hover 效果）

JavaScript:

- 使用了事件监听器（比如表单提交和按钮点击）

- 动态创建和删除 DOM 元素
- 使用了函数来组织代码


### demo2 高级图片库

入口：`demo2/index.html`（按顶部说明用本地服务器打开）

包含以下特性：

- 使用 CSS Grid 创建响应式布局。

- 实现图片懒加载，提高页面加载性能。
- 使用 Intersection Observer 检测图片何时进入视口。
- 应用 CSS 变量来控制布局。
- 实现渐进式图片加载，先显示模糊的占位图，然后加载完整图片。


### demo3 智能家居控制面板

入口：`demo3/index.html`（按顶部说明用本地服务器打开）

一个智能家居设备控制面板，展示模块化前端设计与状态管理实践：

- 设备控制：通过 `modules/lighting.js` / `modules/temperature.js` 控制灯光开关与房间温度（客厅 / 卧室温度滑杆）。
- 天气小部件：`modules/weather.js` 展示实时天气信息。
- 能耗统计：`modules/energy.js` 配合 Chart.js（CDN 引入）绘制能耗图表。
- 自动化规则：`modules/automation.js` 覆盖自动化场景；`modules/notification.js` 处理设备状态通知。
- 待办卡片：页面中附带一个待办事项卡片（`modules/todo.js`）。
- 可拖拽布局：`modules/draggableManager.js` 实现卡片拖拽排布。
- 主题切换：`modules/theme.js` 实现浅色 / 深色主题切换（与 demo1 的 ThemeManager 一脉相承）。
- 数据层：`services/dataService.js` 统一提供设备数据。

### demo4 高级图表仪表板

入口：`demo4/index.html`（按顶部说明用本地服务器打开）

### 项目将包含以下功能：

- 使用 Chart.js 库来绘制图表
- 多种类型的图表展示（折线图、柱状图、饼图等）
- 实时数据更新
- 可交互的图表（悬停效果、点击事件）
- 响应式设计
- 深色/浅色主题切换
- 数据过滤和排序功能

### 设计思路主要围绕以下几个核心原则：

- 模块化设计：

将功能分解成独立的模块（ThemeManager, ChartsManager, DataManager），每个模块负责特定的功能。
这种方法提高了代码的可维护性和可扩展性，使得每个部分都可以独立开发和测试。

- 单一职责原则：

每个模块和类都有明确的单一职责。例如，ThemeManager 只负责主题管理，ChartsManager 只负责图表的创建和更新。
这样的设计使代码更容易理解和维护。

- 封装和抽象：

将复杂的逻辑封装在类和方法中，对外提供简单的接口。
例如，ChartsManager 封装了所有与 Chart.js 相关的操作，使主应用代码不需要直接处理图表细节。

- 事件驱动：

使用事件监听器来响应用户交互（如主题切换、数据过滤）。
这种方法使得界面更加响应式，并且便于添加新的交互功能。

- 响应式设计：

使用 CSS Grid 和媒体查询来创建响应式布局，确保在不同设备上都有良好的显示效果。

- 用户体验优化：

添加加载动画和过渡效果，提供视觉反馈。
实现主题切换功能，满足不同用户的偏好。

- 可配置性：

设计时考虑到可能的配置选项，如图表类型、颜色主题等，为未来的定制化留下空间。

- 代码复用：

通过创建通用的方法（如 createChart）来减少重复代码。


### demo5 卡片式在线编辑器

入口：`demo5/index.html`（按顶部说明用本地服务器打开）

这个项目展示了如何创建一个功能丰富的在线代码编辑器，包括以下特性：

使用 CodeMirror 实现语法高亮和自动补全。
支持 HTML、CSS 和 JavaScript 编辑，并可以在它们之间切换。
实时预览功能，可以立即看到代码的运行结果。
使用 Prettier 实现代码格式化。
支持主题切换，改变编辑器的外观。
使用 LocalStorage 保存代码，在页面刷新后仍能保留。
响应式设计，适应不同的屏幕尺寸。

这个项目的设计思路包括：

模块化：将不同功能拆分为独立的模块（EditorManager、PreviewManager 等），便于维护和扩展。
事件驱动：使用事件监听器响应用户操作，如切换语言、运行代码等。
状态管理：使用 LocalStorage 管理应用状态（保存的代码）。
第三方库集成：集成 CodeMirror 和 Prettier 等库，增强功能。
响应式设计：使用 CSS flexbox 和媒体查询创建响应式布局。

## 长期学习方向

| 阶段 | 学习重点 | 预期产出 |
|---|---|---|
| 基础 | Java、面向对象、集合、异常、Maven | 可独立运行的 Java 示例 |
| Web | Spring Boot、REST API、依赖注入、DTO、校验 | Task HTTP API |
| 数据 | PostgreSQL、JPA、SQL、事务 | 可持久化的 Task 服务 |
| 质量 | JUnit、接口测试、日志、异常处理 | 可验证的后端服务 |
| 交付 | Docker、配置管理、部署、前后端联调 | 可访问的全栈演示 |
| 拓展 | AI 应用接入、RAG 与工程化 | 在后端基础上的 AI 应用实践 |

## 说明

- 本仓库用于个人学习、工程实践与技术积累。
- 教程示例以理解概念为主，部署生产环境前需补充安全、鉴权、并发、配置与测试。
- 欢迎通过 Issues 记录问题、改进建议和学习心得。
