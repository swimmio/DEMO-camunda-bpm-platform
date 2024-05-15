---
title: How do we use Maven in engine-rest/engine-rest-jakarta?
---
This document provides a detailed explanation of how Maven is used in the `engine-rest/engine-rest-jakarta` directory of the Camunda BPM Platform.

<SwmSnippet path="/engine-rest/engine-rest-jakarta/pom.xml" line="1">

---

# Project Information

The `pom.xml` file starts by defining the project information. The `modelVersion` is set to `4.0.0`, which is the standard version for Maven POM files. The `artifactId` is `camunda-engine-rest-core-jakarta`, which is the unique identifier for this project. The `packaging` is set to `jar`, indicating that the project will be packaged as a JAR file.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <artifactId>camunda-engine-rest-core-jakarta</artifactId>
  <name>Camunda Platform - engine - REST Jakarta</name>
  <packaging>jar</packaging>
```

---

</SwmSnippet>

<SwmSnippet path="/engine-rest/engine-rest-jakarta/pom.xml" line="8">

---

# Parent Project

The `parent` element is used to indicate that this POM inherits configurations from a parent POM. The `groupId` is `org.camunda.bpm`, the `artifactId` is `camunda-engine-rest-root`, and the `version` is `7.22.0-SNAPSHOT`. The `relativePath` is set to `../`, indicating that the parent POM is located in the parent directory.

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

<SwmSnippet path="/engine-rest/engine-rest-jakarta/pom.xml" line="15">

---

# Properties

The `properties` element is used to define project-wide properties. Here, `rest.http.port` is set to `38081` and `version.resteasy` is set to `6.2.3.Final`. These properties can be referenced elsewhere in the POM.

```xml
  <properties>
    <rest.http.port>38081</rest.http.port>
    <version.resteasy>6.2.3.Final</version.resteasy>
  </properties>
```

---

</SwmSnippet>

<SwmSnippet path="/engine-rest/engine-rest-jakarta/pom.xml" line="20">

---

# Dependency Management

The `dependencyManagement` element is used to manage the versions of dependencies. Dependencies defined here are not directly included in the project, but their versions are managed centrally. This is useful when multiple modules use the same dependencies to ensure version consistency.

```xml
  <dependencyManagement>
    <dependencies>
      <dependency>
        <groupId>jakarta.platform</groupId>
        <artifactId>jakarta.jakartaee-bom</artifactId>
        <version>${version.jakarta-ee-spec}</version>
        <scope>import</scope>
        <type>pom</type>
      </dependency>
      <dependency>
        <groupId>org.jboss.resteasy</groupId>
        <artifactId>resteasy-bom</artifactId>
        <version>${version.resteasy}</version>
        <type>pom</type>
        <scope>import</scope>
      </dependency>
    </dependencies>
  </dependencyManagement>
```

---

</SwmSnippet>

<SwmSnippet path="/engine-rest/engine-rest-jakarta/pom.xml" line="39">

---

# Dependencies

The `dependencies` element is used to define the actual dependencies of the project. Each `dependency` element specifies a dependency, including its `groupId`, `artifactId`, and `version`. Some dependencies are marked as `provided` or `test`, indicating their scope.

```xml
  <dependencies>

    <dependency>
      <groupId>commons-fileupload</groupId>
      <artifactId>commons-fileupload</artifactId>
      <exclusions>
        <exclusion>
          <groupId>commons-io</groupId>
          <artifactId>commons-io</artifactId>
        </exclusion>
      </exclusions>
    </dependency>
    <!-- override managed version from commons-fileupload -->
    <dependency>
      <groupId>commons-io</groupId>
      <artifactId>commons-io</artifactId>
    </dependency>

    <dependency>
      <groupId>com.fasterxml.jackson.jakarta.rs</groupId>
      <artifactId>jackson-jakarta-rs-json-provider</artifactId>
```

---

</SwmSnippet>

<SwmSnippet path="/engine-rest/engine-rest-jakarta/pom.xml" line="209">

---

# Build Configuration

The `build` element is used to provide build-specific information. This includes the configuration of various build plugins, such as the `maven-dependency-plugin`, `maven-resources-plugin`, `transformer-maven-plugin`, `build-helper-maven-plugin`, `maven-source-plugin`, `maven-jar-plugin`, `maven-war-plugin`, `maven-surefire-plugin`, and `shrinkwrap-resolver-maven-plugin`.

```xml
  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-dependency-plugin</artifactId>
        <executions>
          <execution>
            <phase>initialize</phase>
            <goals>
              <goal>properties</goal>
            </goals>
          </execution>
        </executions>
      </plugin>

      <plugin>
        <artifactId>maven-resources-plugin</artifactId>
        <executions>
          <!-- copy main sources & resources -->
          <execution>
            <id>copy-main-sources</id>
```

---

</SwmSnippet>

<SwmSnippet path="/engine-rest/engine-rest-jakarta/pom.xml" line="506">

---

# Profiles

The `profiles` element is used to provide different build settings for different environments. Each `profile` element defines a set of configurations that can be activated under certain conditions. This includes `resteasy`, `wildfly-compatibility`, `below-jdk17`, and `jdk17-and-onwards` profiles.

```xml
  <profiles>
    <profile>
      <id>resteasy</id>
      <activation>
        <activeByDefault>true</activeByDefault>
      </activation>

      <properties>
        <version.netty>4.1.89.Final</version.netty>
        <version.undertow>2.3.0.Final</version.undertow>
      </properties>

      <dependencies>
        <dependency>
          <groupId>io.undertow</groupId>
          <artifactId>undertow-servlet</artifactId>
          <version>${version.undertow}</version>
          <scope>test</scope>
        </dependency>
        <dependency>
          <groupId>org.jboss.resteasy</groupId>
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
