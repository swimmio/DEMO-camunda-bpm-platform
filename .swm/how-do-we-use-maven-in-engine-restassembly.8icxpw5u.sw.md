---
title: How do we use Maven in engine-rest/assembly?
---
This document provides a detailed walkthrough of how Maven is used in the `engine-rest/assembly` directory of the Camunda BPM Platform project.

<SwmSnippet path="/engine-rest/assembly/pom.xml" line="1">

---

# Maven Project Configuration

The `pom.xml` file starts by defining the project and its model version. It specifies the artifactId as `camunda-engine-rest` and the packaging type as `war`. The parent project is defined with groupId `org.camunda.bpm` and artifactId `camunda-engine-rest-root`.

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <artifactId>camunda-engine-rest</artifactId>
  <name>Camunda Platform - engine - REST - Assembly</name>
  <packaging>war</packaging>

  <parent>
    <groupId>org.camunda.bpm</groupId>
    <artifactId>camunda-engine-rest-root</artifactId>
    <relativePath>../</relativePath>
    <version>7.22.0-SNAPSHOT</version>
  </parent>
```

---

</SwmSnippet>

<SwmSnippet path="/engine-rest/assembly/pom.xml" line="14">

---

# Maven Properties

The properties section defines whether to skip the generation of a bill of materials (BOM) for the license book and the scopes for the third-party BOM. Here, the BOM generation is not skipped and the scopes are set to `compile|provided`.

```xml
  <properties>
    <!-- generate a bom of dependencies for the license book.
    We include compile and provided scope dependencies; 
    all the dependencies that we include in only one of the 
    runtime-specific-WARs are in provided scope -->
    <skip-third-party-bom>false</skip-third-party-bom>
    <third-party-bom-scopes>compile|provided</third-party-bom-scopes>
  </properties>
```

---

</SwmSnippet>

<SwmSnippet path="/engine-rest/assembly/pom.xml" line="23">

---

# Maven Dependencies

The dependencies section lists all the dependencies required for the project. These include `camunda-engine-rest-core` and various other dependencies like `resteasy-jaxrs`, `jersey-container-servlet`, and `jersey-hk2`. The scope for these dependencies is set to `provided`.

```xml
  <dependencies>
    <dependency>
      <groupId>org.camunda.bpm</groupId>
      <artifactId>camunda-engine-rest-core</artifactId>
      <version>${project.version}</version>
    </dependency>

    <!-- dependencies only used for assemblies should be scope provided -->
    <dependency>
      <groupId>org.camunda.bpm</groupId>
      <artifactId>camunda-engine-rest-core</artifactId>
      <version>${project.version}</version>
      <classifier>sources</classifier>
      <scope>provided</scope>
    </dependency>

    <dependency>
      <groupId>org.camunda.bpm</groupId>
      <artifactId>camunda-engine-rest-core</artifactId>
      <version>${project.version}</version>
      <classifier>tests</classifier>
```

---

</SwmSnippet>

<SwmSnippet path="/engine-rest/assembly/pom.xml" line="69">

---

# Maven Build Configuration

The build section defines the plugins used during the build process. The `maven-assembly-plugin` is used here with multiple executions for different environments like `wildfly`, `tomcat`, `was`, `wls`, and others. Each execution has its own configuration, including the final name of the build, the output directory, and the work directory.

```xml
  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-assembly-plugin</artifactId>
        <executions>
          <execution>
            <id>wildfly</id>
            <phase>package</phase>
            <goals>
              <goal>single</goal>
            </goals>
            <configuration>
              <archive>
                <manifestEntries>
                  <!-- module dependencies for deployment on wildfly  -->
                  <Dependencies>org.camunda.bpm.camunda-engine,org.camunda.bpm.dmn.camunda-engine-dmn,org.camunda.commons.camunda-commons-logging,org.camunda.spin.camunda-spin-core,org.camunda.bpm.juel.camunda-juel services,org.graalvm.js.js-scriptengine services</Dependencies>
                </manifestEntries>
              </archive>
              <descriptors>
                <descriptor>assembly-war-wildfly.xml</descriptor>
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
