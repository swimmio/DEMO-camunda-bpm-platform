---
title: Maven Configuration in engine-rest/engine-rest
---
This document provides a detailed explanation of how Maven is used in the `engine-rest/engine-rest` directory of the Camunda BPM Platform.

<SwmSnippet path="/engine-rest/engine-rest/pom.xml" line="1">

---

# Maven Project Configuration

The `pom.xml` file starts by defining the project as a Maven project. The `modelVersion` is set to `4.0.0`, which is the latest model version. The `artifactId` is set to `camunda-engine-rest-core`, which is the identifier of the project artifact. The `name` is set to `Camunda Platform - engine - REST`, which is the display name of the project. The `packaging` is set to `jar`, which means the project will be packaged as a JAR file.

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <artifactId>camunda-engine-rest-core</artifactId>
  <name>Camunda Platform - engine - REST</name>
  <packaging>jar</packaging>
```

---

</SwmSnippet>

<SwmSnippet path="/engine-rest/engine-rest/pom.xml" line="7">

---

# Parent Project Configuration

The `parent` element is used to indicate the parent project from which this project inherits. The `groupId` is set to `org.camunda.bpm`, which is the identifier of the parent project's group. The `artifactId` is set to `camunda-engine-rest-root`, which is the identifier of the parent project's artifact. The `relativePath` is set to `../`, which is the location of the parent project's `pom.xml` file relative to this project's `pom.xml` file. The `version` is set to `7.22.0-SNAPSHOT`, which is the version of the parent project.

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

<SwmSnippet path="/engine-rest/engine-rest/pom.xml" line="14">

---

# Project Properties Configuration

The `properties` element is used to define project-wide properties that can be referenced elsewhere in the `pom.xml` file. The `version.tomcat` property is set to `7.0.50`, which is the version of Tomcat to be used. The `rest.http.port` property is set to `38080`, which is the port on which the REST service will be available. The `javax.activation.version` property is set to `1.1.1`, which is the version of the Java Activation Framework to be used.

```xml
  <properties>
    <!-- pin tomcat version for engine-rest -->
    <version.tomcat>7.0.50</version.tomcat>
    <rest.http.port>38080</rest.http.port>
    <javax.activation.version>1.1.1</javax.activation.version>
  </properties>
```

---

</SwmSnippet>

<SwmSnippet path="/engine-rest/engine-rest/pom.xml" line="21">

---

# Project Dependencies Configuration

The `dependencies` element is used to define the dependencies of the project. Each `dependency` element specifies a single dependency. The `groupId` and `artifactId` elements identify the project that is depended on. The `version` element specifies the version of the project that is depended on. The `scope` element specifies the classpath of the dependency, and the `exclusions` element is used to exclude certain transitive dependencies.

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
      <groupId>com.fasterxml.jackson.jaxrs</groupId>
      <artifactId>jackson-jaxrs-json-provider</artifactId>
      <!--
```

---

</SwmSnippet>

<SwmSnippet path="/engine-rest/engine-rest/pom.xml" line="247">

---

# Build Configuration

The `build` element is used to provide build-specific information. The `testResources` element is used to specify resources that are used for testing. The `plugins` element is used to specify build plugins. Each `plugin` element specifies a single build plugin. The `groupId` and `artifactId` elements identify the plugin. The `executions` element is used to configure the executions of the plugin. Each `execution` element specifies a single execution of the plugin. The `goals` element is used to specify the goals of the plugin execution.

```xml
  <build>
    <testResources>
      <testResource>
        <directory>src/test/resources</directory>
        <filtering>true</filtering>
      </testResource>
    </testResources>

    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-source-plugin</artifactId>
        <executions>
          <execution>
            <!-- This id must match the -Prelease-profile id value or else sources will be "uploaded" twice, which causes Nexus to fail -->
            <id>attach-sources</id>
            <goals>
              <goal>jar</goal>
            </goals>
          </execution>
        </executions>
```

---

</SwmSnippet>

<SwmSnippet path="/engine-rest/engine-rest/pom.xml" line="316">

---

# Profiles Configuration

The `profiles` element is used to provide profile-specific information. Each `profile` element specifies a single profile. The `id` element is used to identify the profile. The `properties`, `dependencies`, and `build` elements are used to specify profile-specific properties, dependencies, and build information, respectively.

```xml
  <profiles>
    <profile>
      <id>distro</id>
      <dependencies>
        <dependency>
          <groupId>org.jboss.spec.javax.ws.rs</groupId>
          <artifactId>jboss-jaxrs-api_2.1_spec</artifactId>
          <scope>provided</scope>
        </dependency>
      </dependencies>
      <build>
        <plugins>
          <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-surefire-plugin</artifactId>
            <configuration>
              <skipTests>true</skipTests>
            </configuration>
          </plugin>
        </plugins>
      </build>
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
