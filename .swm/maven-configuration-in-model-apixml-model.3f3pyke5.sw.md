---
title: Maven Configuration in model-api/xml-model
---
This document provides a detailed explanation of how Maven is used in the `model-api/xml-model` directory of the project.

<SwmSnippet path="/model-api/xml-model/pom.xml" line="1">

---

# Project Information

The `pom.xml` file starts by defining the project and its model version. It then specifies the parent project, which is `camunda-model-apis`. The artifact of this project is `camunda-xml-model` and it is packaged as a jar. The name of the project is `Camunda Platform - Xml Model API` and it was started in 2014.

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <parent>
    <groupId>org.camunda.bpm.model</groupId>
    <artifactId>camunda-model-apis</artifactId>
    <relativePath>../</relativePath>
    <version>7.22.0-SNAPSHOT</version>
  </parent>

  <artifactId>camunda-xml-model</artifactId>
  <packaging>jar</packaging>

  <name>Camunda Platform - Xml Model API</name>
  <inceptionYear>2014</inceptionYear>
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/xml-model/pom.xml" line="23">

---

# Dependencies

The project has two dependencies: `junit` and `assertj-core`. Both are provided in the scope, meaning they are only required for compiling the project code and are not included in the runtime environment.

```xml
  <dependencies>

    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <scope>provided</scope>
    </dependency>

    <dependency>
      <groupId>org.assertj</groupId>
      <artifactId>assertj-core</artifactId>
      <scope>provided</scope>
    </dependency>

  </dependencies>
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/xml-model/pom.xml" line="39">

---

# Build Configuration

The build configuration includes the `maven-bundle-plugin` from `org.apache.felix`. This plugin is used to generate sources and process classes. The `cleanVersions` goal is used to clean up the versions of the project's dependencies, and the `manifest` goal is used to generate the Manifest file for the project.

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

<SwmSnippet path="/model-api/xml-model/pom.xml" line="64">

---

# API Compatibility Check

The project includes a profile for checking API compatibility. The `clirr-maven-plugin` is used to compare the current project version with the old version specified in `camunda.version.old`. The plugin generates a report of the API differences and logs the results. The `check-no-fork` goal is used to check the API without forking the build lifecycle.

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
                <exclude>org/camunda/bpm/model/xml/impl/**</exclude>
              </excludes>
            </configuration>
            <executions>
              <execution>
                <id>all</id>
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
