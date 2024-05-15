---
title: XML Implementation in Camunda BPM Platform
---
This document will cover the XML Implementation in the Camunda BPM Platform, specifically focusing on:

1. The role and usage of XML Implementation in the codebase
2. The key classes and methods involved in XML Implementation

# XML Implementation in the Codebase

XML Implementation in the Camunda BPM Platform is primarily handled through the `IoUtil` class, which provides utility methods for XML document manipulation. This includes converting XML documents to strings, writing XML documents to output streams, and transforming XML documents to XML output.

<SwmSnippet path="/model-api/xml-model/src/main/java/org/camunda/bpm/model/xml/impl/util/IoUtil.java" line="95">

---

# Key Classes and Methods in XML Implementation

The `convertXmlDocumentToString` method in the `IoUtil` class is a key part of XML Implementation. It converts a `DomDocument` to its String representation by transforming the DOM to XML and writing the result to a `StreamResult`.

```java
  /**
   * Converts a {@link DomDocument} to its String representation
   *
   * @param document  the XML document to convert
   */
  public static String convertXmlDocumentToString(DomDocument document) {
    StringWriter stringWriter = new StringWriter();
    StreamResult result = new StreamResult(stringWriter);
    transformDocumentToXml(document, result);
    return stringWriter.toString();
  }
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/xml-model/src/main/java/org/camunda/bpm/model/xml/impl/util/IoUtil.java" line="118">

---

The `transformDocumentToXml` method in the `IoUtil` class is another crucial part of XML Implementation. It transforms a `DomDocument` to XML output by creating a new transformer and setting its output properties. The transformer then transforms the document's `DomSource` to the provided `StreamResult`.

```java
  /**
   * Transforms a {@link DomDocument} to XML output.
   *
   * @param document  the DOM document to transform
   * @param result  the {@link StreamResult} to write to
   */
  public static void transformDocumentToXml(DomDocument document, StreamResult result) {
    TransformerFactory transformerFactory = TransformerFactory.newInstance();
    try {
      Transformer transformer = transformerFactory.newTransformer();
      transformer.setOutputProperty(OutputKeys.ENCODING, "UTF-8");
      transformer.setOutputProperty(OutputKeys.INDENT, "yes");
      transformer.setOutputProperty("{http://xml.apache.org/xslt}indent-amount", "2");

      synchronized(document) {
        transformer.transform(document.getDomSource(), result);
      }
    } catch (TransformerConfigurationException e) {
      throw new ModelIoException("Unable to create a transformer for the model", e);
    } catch (TransformerException e) {
      throw new ModelIoException("Unable to transform model to xml", e);
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
