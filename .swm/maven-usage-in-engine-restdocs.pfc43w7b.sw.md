---
title: Maven Usage in engine-rest/docs
---
This document provides a detailed walkthrough of how Maven is used in the `engine-rest/docs` directory of the project. It focuses on the configuration and execution steps defined in the `pom.xml` file.

<SwmSnippet path="/engine-rest/docs/pom.xml" line="1">

---

# Project Configuration

The `pom.xml` file starts with the project configuration. It specifies the parent artifact as `camunda-engine-rest-root` and the current artifact as `docs`. The packaging type is set to `pom`, indicating that this project is expected to be a collection of other projects.

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">

  <parent>
    <artifactId>camunda-engine-rest-root</artifactId>
    <groupId>org.camunda.bpm</groupId>
    <version>7.22.0-SNAPSHOT</version>
  </parent>
  <modelVersion>4.0.0</modelVersion>

  <artifactId>docs</artifactId>
  <name>Camunda Platform - engine - REST - Docs</name>
  <packaging>pom</packaging>

  <properties>
```

---

</SwmSnippet>

<SwmSnippet path="/engine-rest/docs/pom.xml" line="18">

---

# Dependencies

The project declares a dependency on `camunda-engine-rest-openapi`. This dependency is necessary for generating the REST API documentation.

```xml
  <dependencies>
    <dependency>
      <groupId>org.camunda.bpm</groupId>
      <artifactId>camunda-engine-rest-openapi</artifactId>
      <version>${project.version}</version>
    </dependency>
  </dependencies>
```

---

</SwmSnippet>

<SwmSnippet path="/engine-rest/docs/pom.xml" line="26">

---

# Build Configuration

The build configuration includes two plugins. The `maven-dependency-plugin` is used to unpack the `camunda-engine-rest-openapi` artifact during the `generate-resources` phase.

```xml
  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-dependency-plugin</artifactId>
        <executions>
          <execution>
            <id>unpack</id>
            <phase>generate-resources</phase>
            <goals>
              <goal>unpack</goal>
            </goals>
            <configuration>
              <artifactItems>
                <artifactItem>
                  <groupId>org.camunda.bpm</groupId>
                  <artifactId>camunda-engine-rest-openapi</artifactId>
                  <version>${project.version}</version>
                  <type>jar</type>
                </artifactItem>
              </artifactItems>
```

---

</SwmSnippet>

<SwmSnippet path="/engine-rest/docs/pom.xml" line="51">

---

# Frontend Plugin Configuration

The `frontend-maven-plugin` is used to manage frontend resources. It installs Node and npm, runs `npm install` to install Node.js dependencies, and executes `npm run build` to build the project.

```xml
      <plugin>
        <groupId>com.github.eirslett</groupId>
        <artifactId>frontend-maven-plugin</artifactId>
        <configuration>
          <outputdir>${project.build.directory}</outputdir>
        </configuration>
        <executions>
          <execution>
            <id>install node and npm</id>
            <goals>
              <goal>install-node-and-npm</goal>
            </goals>
          </execution>
          <execution>
            <id>npm install</id>
            <goals>
              <goal>npm</goal>
            </goals>
            <phase>generate-resources</phase>
            <configuration>
              <arguments>ci</arguments>
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
