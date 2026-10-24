# Day 8｜Maven 与 pom.xml

> 原课程日期：2026-10-18  
> 学习时间：约 10 分钟  
> 连续项目：Task 任务管理系统。课程日期与 Git 实际提交时间分别记录。

## 核心知识（2 分钟）
Maven 相当于 Java 生态的项目构建与依赖管理工具，`pom.xml` 类似前端 `package.json`，但并非一一对应。常用命令：`mvn compile`、`mvn test`、`mvn package`。

## 可运行示例（4 分钟）
把前一课代码移入 `src/main/java/com/example/task/`，创建 `pom.xml`：
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>task-app</artifactId>
  <version>0.1.0-SNAPSHOT</version>
  <properties>
    <maven.compiler.release>17</maven.compiler.release>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
  </properties>
  <build><plugins>
    <plugin>
      <groupId>org.codehaus.mojo</groupId>
      <artifactId>exec-maven-plugin</artifactId>
      <version>3.6.4</version>
      <configuration><mainClass>com.example.task.Main</mainClass></configuration>
    </plugin>
  </plugins></build>
</project>
```
运行：`mvn compile exec:java`，执行上一课的 Main 程序。

## 实践题（2 分钟）
解释 groupId、artifactId、version 的含义，并修改项目版本为 0.2.0-SNAPSHOT。

## 参考答案与解析（2 分钟）
`<version>0.2.0-SNAPSHOT</version>`。groupId 是组织标识，artifactId 是项目标识，version 是构件版本。Maven 标准目录是 `src/main/java` 和 `src/test/java`。下一课引入 Spring Boot。
