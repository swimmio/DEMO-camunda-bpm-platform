---
title: Maven Configuration in model-api/cmmn-model
---
This document provides a detailed explanation of how Maven is used in the `model-api/cmmn-model` directory of the Camunda BPM Platform.

<SwmSnippet path="/model-api/cmmn-model/pom.xml" line="1">

---

# Maven Project Configuration

The `pom.xml` file starts by defining the project as a Maven project. It specifies the model version as `4.0.0`. The parent project is defined as `camunda-model-apis` with version `7.22.0-SNAPSHOT`. The artifact for this project is `camunda-cmmn-model` and it is packaged as a `jar` file.

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <parent>
    <groupId>org.camunda.bpm.model</groupId>
    <artifactId>camunda-model-apis</artifactId>
    <relativePath>../</relativePath>
    <version>7.22.0-SNAPSHOT</version>
  </parent>

  <artifactId>camunda-cmmn-model</artifactId>
  <packaging>jar</packaging>

  <name>Camunda Platform - CMMN Model API</name>
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/cmmn-model/pom.xml" line="16">

---

# Maven Properties Configuration

The properties section defines the artifact as `org.camunda.bpm.model.cmmn` and specifies the OSGi export configurations.

```xml
  <properties>
    <camunda.artifact>org.camunda.bpm.model.cmmn</camunda.artifact>
    <camunda.osgi.export>
      !org.camunda.bpm.model.cmmn.schema.*,
      ${camunda.osgi.export.pkg};${camunda.osgi.version};-noimport:=true
    </camunda.osgi.export>
  </properties>
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/cmmn-model/pom.xml" line="23">

---

# Maven Dependencies Configuration

The dependencies section lists all the dependencies required for this project. It includes `camunda-xml-model`, `junit`, `assertj-core`, and `camunda-bpm-archunit`.

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

<SwmSnippet path="/model-api/cmmn-model/pom.xml" line="51">

---

# Maven Build Configuration

The build section defines the plugins used during the build process. It includes the `maven-bundle-plugin` and `maven-surefire-plugin`.

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

<SwmSnippet path="/model-api/cmmn-model/pom.xml" line="84">

---

# Maven Profiles Configuration

The profiles section defines a profile `check-api-compatibility` which is activated by default. It uses the `clirr-maven-plugin` to check for API differences between the latest minor release.

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
                <exclude>org/camunda/bpm/model/cmmn/impl/**</exclude>
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
