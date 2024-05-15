---
title: Exploring the Mapping Between Templates and Endpoints
---
This document will cover the mapping logic between templates and endpoints in the Camunda Platform. We'll cover:

1. The role of the TemplateParser class
2. The process of creating template data
3. The logic behind resolving paths and models

<SwmSnippet path="/engine-rest/engine-rest-openapi-generator/src/main/java/org/camunda/bpm/engine/rest/openapi/generator/impl/TemplateParser.java" line="47">

---

# The Role of the TemplateParser Class

The `TemplateParser` class is responsible for parsing templates and generating output files. It takes four arguments: source template directory, main template, output directory, and intermediate output directory. It uses the FreeMarker library to process the templates.

```java
public class TemplateParser {

  public static void main(String[] args) throws IOException, TemplateException {

    if (args.length != 4) {
      throw new RuntimeException(
          "Must provide four arguments: "
          + "<source template directory> "
          + "<main template> "
          + "<output directory> "
          + "<intermediate output dir>");
    }

    String sourceDirectory = args[0];
    String mainTemplate = args[1];
    String outputFile = args[2];
    String debugFile = args[3];

    Configuration cfg = new Configuration(Configuration.VERSION_2_3_29);

    cfg.setDirectoryForTemplateLoading(new File(sourceDirectory));
```

---

</SwmSnippet>

<SwmSnippet path="/engine-rest/engine-rest-openapi-generator/src/main/java/org/camunda/bpm/engine/rest/openapi/generator/impl/TemplateParser.java" line="94">

---

# Creating Template Data

The `createTemplateData` method is used to create a map of template data. It resolves versions, models, and endpoints, and puts them into the map. The models and endpoints are resolved from the source directory.

```java
  protected static Map<String, Object> createTemplateData(String sourceDirectory)
      throws IOException {
    Map<String, Object> templateData = new HashMap<>();

    resolveVersions(templateData);
    Map<String, String> models = resolveModels(sourceDirectory);
    templateData.put("models", models);
    Map<String, List<String>> endpoints = resolvePaths(sourceDirectory);
    templateData.put("endpoints", endpoints);

    return templateData;
  }
```

---

</SwmSnippet>

<SwmSnippet path="/engine-rest/engine-rest-openapi-generator/src/main/java/org/camunda/bpm/engine/rest/openapi/generator/impl/TemplateParser.java" line="179">

---

# Resolving Paths and Models

The `resolvePaths` method is used to resolve the paths of the endpoints. It creates a map of endpoint paths and HTTP methods pairs. The paths are resolved from the source directory. The `resolveModels` method is used to resolve the models from the source directory. It returns a map of model name and file path to it.

```java
  /**
   * 
   * @param sourceDirectory the template directory that stores the endpoints
   * @return a map of endpoint path and HTTP methods pairs,
   * the map is ordered lexicographically by the endpoint paths
   * the list of methods is ordered as well
   */
  protected static Map<String, List<String>> resolvePaths(String sourceDirectory) {
    File endpointsDir = new File(sourceDirectory + "/paths");
    int endpointStartAt = endpointsDir.getAbsolutePath().length();
    Collection<File> endpointsFiles = FileUtils.listFiles(
        endpointsDir, 
        new RegexFileFilter("^(.*?)"), 
        DirectoryFileFilter.DIRECTORY
        );

    Map<String, List<String>> endpoints = new TreeMap<>();
    for (File file : endpointsFiles) {
      String endpointMethod = FilenameUtils.removeExtension(file.getName());
      String filePath = file.getAbsolutePath();
      String endpointPath = filePath
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
