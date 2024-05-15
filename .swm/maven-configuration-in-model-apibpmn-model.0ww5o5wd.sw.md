---
title: Maven Configuration in model-api/bpmn-model
---
This document covers the usage of Maven in the `model-api/bpmn-model` directory of the project. It will explain the Maven configuration file `pom.xml` and how it is used to build and manage the project.

<SwmSnippet path="/model-api/bpmn-model/pom.xml" line="1">

---

# Project Information

The `pom.xml` file starts with the project information. It specifies the model version, parent artifact details, and the artifact details for this project. The `artifactId` is set to `camunda-bpmn-model` and the packaging type is `jar`. The name of the project is `Camunda Platform - BPMN Model API` and it was started in 2014.

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <parent>
    <groupId>org.camunda.bpm.model</groupId>
    <artifactId>camunda-model-apis</artifactId>
    <relativePath>../</relativePath>
    <version>7.22.0-SNAPSHOT</version>
  </parent>

  <artifactId>camunda-bpmn-model</artifactId>
  <packaging>jar</packaging>

  <name>Camunda Platform - BPMN Model API</name>
  <inceptionYear>2014</inceptionYear>
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/bpmn-model/pom.xml" line="16">

---

# Project Properties

The properties section defines some project-specific properties. The `camunda.artifact` property is set to `org.camunda.bpm.model.bpmn` and the `camunda.osgi.export` property is set to exclude the `org.camunda.bpm.model.bpmn.schema` package from OSGi exports.

```xml
  <properties>
    <camunda.artifact>org.camunda.bpm.model.bpmn</camunda.artifact>
    <camunda.osgi.export>
      !org.camunda.bpm.model.bpmn.schema,
      ${camunda.osgi.export.pkg};${camunda.osgi.version};-noimport:=true
    </camunda.osgi.export>
  </properties>
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/bpmn-model/pom.xml" line="23">

---

# Project Dependencies

The dependencies section lists all the dependencies required by this project. It includes `camunda-xml-model`, `junit`, `assertj-core`, and `camunda-bpm-archunit` as dependencies. The scope of `junit` and `assertj-core` is set to `test`, indicating that they are required for running tests.

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
      <groupId>org.camunda.bpm</groupId>
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/bpmn-model/pom.xml" line="51">

---

# Build Configuration

The build section defines the build configuration for the project. It specifies the plugins to be used during the build process. The `maven-bundle-plugin` is used to generate sources and manifest files. The `maven-surefire-plugin` is used to scan dependencies during the build process.

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

<SwmSnippet path="/model-api/bpmn-model/pom.xml" line="84">

---

# Profile Configuration

The profiles section defines a profile with the id `check-api-compatibility`. This profile is activated by default and includes a plugin configuration for the `clirr-maven-plugin`. This plugin is used to check for API differences between the latest minor release and the current project version.

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
                <exclude>org/camunda/bpm/model/bpmn/impl/**</exclude>
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
