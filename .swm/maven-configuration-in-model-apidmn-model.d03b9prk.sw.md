---
title: Maven Configuration in model-api/dmn-model
---
This document provides a detailed walkthrough of how Maven is used in the `model-api/dmn-model` directory of the project.

<SwmSnippet path="/model-api/dmn-model/pom.xml" line="1">

---

# Project Configuration

The `pom.xml` file starts by defining the project and its model version. It then specifies the parent project, which is `camunda-model-apis`. The artifact for this project is `camunda-dmn-model` and it is packaged as a jar file. The name of the project is `Camunda Platform - DMN Model API`.

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <parent>
    <groupId>org.camunda.bpm.model</groupId>
    <artifactId>camunda-model-apis</artifactId>
    <relativePath>../</relativePath>
    <version>7.22.0-SNAPSHOT</version>
  </parent>

  <artifactId>camunda-dmn-model</artifactId>
  <packaging>jar</packaging>

  <name>Camunda Platform - DMN Model API</name>
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/dmn-model/pom.xml" line="23">

---

# Dependencies

The `pom.xml` file specifies the dependencies for the project. These include `camunda-xml-model`, `junit`, `assertj-core`, `xmlunit-core`, and `camunda-bpm-archunit`. The scope of the test dependencies is set to `test`, meaning they are only required for testing.

```xml
  <dependencies>

    <dependency>
      <groupId>org.camunda.bpm.model</groupId>
      <artifactId>camunda-xml-model</artifactId>
    </dependency>

    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <scope>test</scope>
    </dependency>

    <dependency>
      <groupId>org.assertj</groupId>
      <artifactId>assertj-core</artifactId>
      <scope>test</scope>
    </dependency>

    <dependency>
      <groupId>org.xmlunit</groupId>
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/dmn-model/pom.xml" line="57">

---

# Build Configuration

The build configuration includes plugins such as `maven-bundle-plugin` and `maven-surefire-plugin`. The `maven-bundle-plugin` is used to generate sources and process classes. The `maven-surefire-plugin` is used to scan dependencies during the build process.

```xml
  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.felix</groupId>
        <artifactId>maven-bundle-plugin</artifactId>
        <executions>
          <execution>
            <phase>generate-sources</phase>
            <goals>
              <goal>cleanVersions</goal>
            </goals>
          </execution>
          <execution>
            <id>bundle-manifest</id>
            <phase>process-classes</phase>
            <goals>
              <goal>manifest</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/dmn-model/pom.xml" line="90">

---

# API Compatibility Check

The `pom.xml` file also includes a profile for checking API compatibility. This uses the `clirr-maven-plugin` to compare the current version of the project with an older version. The configuration specifies what to exclude from the check and how to handle warnings and errors.

```xml
  <profiles>
    <profile>
      <id>check-api-compatibility</id>
      <activation>
        <activeByDefault>true</activeByDefault>
      </activation>
      <build>
        <plugins>
          <plugin>
            <groupId>org.codehaus.mojo</groupId>
            <artifactId>clirr-maven-plugin</artifactId>
            <configuration>
              <comparisonVersion>${camunda.version.old}</comparisonVersion>
              <logResults>true</logResults>
              <excludes>
                <exclude>org/camunda/bpm/model/dmn/impl/**</exclude>
                <exclude>org/camunda/bpm/model/dmn/instance/Binding</exclude>
                <exclude>org/camunda/bpm/model/dmn/instance/ParameterReference</exclude>
              </excludes>
            </configuration>
            <executions>
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
