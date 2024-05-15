---
title: How do we use Maven in engine-rest/engine-rest-openapi?
---
This document provides a detailed walkthrough of how Maven is used in the `engine-rest/engine-rest-openapi` directory of the project.

<SwmSnippet path="/engine-rest/engine-rest-openapi/pom.xml" line="1">

---

# Maven Project Configuration

The `pom.xml` file starts by defining the model version, artifact ID, name, and packaging type. The artifact ID `camunda-engine-rest-openapi` is unique within a group ID. The packaging type is `jar`, which means the build produces a JAR.

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <artifactId>camunda-engine-rest-openapi</artifactId>
  <name>Camunda Platform - engine - REST - OpenAPI</name>
  <packaging>jar</packaging>
```

---

</SwmSnippet>

<SwmSnippet path="/engine-rest/engine-rest-openapi/pom.xml" line="7">

---

# Parent Project

The `parent` element is used to indicate this project's parent project. The parent project is `camunda-engine-rest-root` with a group ID of `org.camunda.bpm`. The version of the parent project is `7.22.0-SNAPSHOT`.

```xml
  <parent>
    <groupId>org.camunda.bpm</groupId>
    <artifactId>camunda-engine-rest-root</artifactId>
    <relativePath>../</relativePath>
    <version>7.22.0-SNAPSHOT</version>
  </parent>
```

---

</SwmSnippet>

<SwmSnippet path="/engine-rest/engine-rest-openapi/pom.xml" line="14">

---

# Properties

The `properties` element is used to define project-wide properties. These properties include the directory for generated sources, the OpenAPI generator version, and versions of various dependencies.

```xml
  <properties>
    <generated-directory>${project.build.directory}/generated-sources/openapi-json</generated-directory>
    <generated-file>openapi.json</generated-file>

    <openapi.generator.version>4.2.3</openapi.generator.version>
    <!-- properties versions used by the openapi client -->
    <!-- update them during openapi.generator version update  -->
    <gson-fire-version>1.8.3</gson-fire-version>
    <swagger-core-version>1.5.22</swagger-core-version>
    <okhttp-version>3.14.2</okhttp-version>
    <gson-version>2.8.9</gson-version>
    <commons-lang3-version>3.9</commons-lang3-version>
    <maven-plugin-version>1.0.0</maven-plugin-version>
    <javax-annotation-version>1.0</javax-annotation-version>
    <junit-version>4.13.1</junit-version>
  </properties>
```

---

</SwmSnippet>

<SwmSnippet path="/engine-rest/engine-rest-openapi/pom.xml" line="31">

---

# Dependencies

The `dependencies` element is used to list all dependencies required by the project. This includes the `camunda-engine-rest-openapi-generator` artifact for test scope, various test dependencies, and dependencies required by the OpenAPI client.

```xml
  <dependencies>

    <dependency>
      <groupId>org.camunda.bpm</groupId>
      <artifactId>camunda-engine-rest-openapi-generator</artifactId>
      <scope>test</scope>
      <version>${project.version}</version>
    </dependency>

    <!-- test dependencies -->
    <dependency>
      <groupId>org.slf4j</groupId>
      <artifactId>slf4j-jdk14</artifactId>
      <scope>test</scope>
    </dependency>
    <dependency>
      <groupId>com.github.tomakehurst</groupId>
      <artifactId>wiremock</artifactId>
      <version>${version.wiremock}</version>
      <scope>test</scope>
    </dependency>
```

---

</SwmSnippet>

<SwmSnippet path="/engine-rest/engine-rest-openapi/pom.xml" line="120">

---

# Build Configuration

The `build` element is used to provide build-specific information. This includes the configuration of various plugins such as the `exec-maven-plugin`, `build-helper-maven-plugin`, and `openapi-generator-maven-plugin`.

```xml
  <build>
    <plugins>
      <plugin>
        <groupId>org.codehaus.mojo</groupId>
        <artifactId>exec-maven-plugin</artifactId>
        <executions>
          <execution>
            <id>generate-openapi-json</id>
            <phase>generate-resources</phase>
            <goals>
              <goal>java</goal>
            </goals>
            <configuration>
              <classpathScope>test</classpathScope>
              <mainClass>org.camunda.bpm.engine.rest.openapi.generator.impl.TemplateParser</mainClass>
              <arguments>
                <argument>${project.basedir}/src/main/templates</argument>
                <argument>main.ftl</argument>
                <argument>${generated-directory}/${generated-file}</argument>
                <argument>${project.build.directory}</argument>
              </arguments>
```

---

</SwmSnippet>

<SwmSnippet path="/engine-rest/engine-rest-openapi/pom.xml" line="222">

---

# Profiles

The `profiles` element is used to provide a set of configurations that can be activated under certain conditions. Here, a profile with the ID `javadocs` is defined, which modifies the build configuration when activated.

```xml
  <profiles>
    <profile>
      <id>javadocs</id>
      <build>
        <plugins>
          <plugin>
            <groupId>org.openapitools</groupId>
            <artifactId>openapi-generator-maven-plugin</artifactId>
            <version>${openapi.generator.version}</version>
            <configuration>
              <skip>true</skip>
            </configuration>
          </plugin>
          
          <plugin>
            <artifactId>maven-compiler-plugin</artifactId>
            <executions>
              <execution>
                <id>default-testCompile</id>
                <goals>
                  <goal>testCompile</goal>
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
