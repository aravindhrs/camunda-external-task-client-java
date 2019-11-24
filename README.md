# Camunda External Task Client (Java)


[![Maven Central](https://maven-badges.herokuapp.com/maven-central/org.camunda.bpm/camunda-external-task-client/badge.svg)](https://maven-badges.herokuapp.com/maven-central/org.camunda.bpm/camunda-external-task-client)


The **Camunda External Task Client (Java)** allows to set up remote Service Tasks for your workflow.

* [Quick Start](https://docs.camunda.org/get-started/quick-start/)
* [Documentation](https://docs.camunda.org/manual/develop/user-guide/ext-client/)
* [Examples](https://github.com/camunda/camunda-external-task-client-java/tree/master/examples)

## Features
* Complete External Tasks
* Extend the lock duration of External Tasks
* Unlock External Tasks
* Report BPMN errors as well as failures
* Share primitive and object typed process variables with the Workflow Engine

### Howto use typed variables
```java
JsonValue jsonCustomer = externalTask.getVariableTyped("customer");
// deserialize to customer object and modify
variables.put("customer", ClientValues.jsonValue(customerJsonString));

XmlValue xmlContract = externalTask.getvariableTyped("contract");
// deserialize to contract object and modify value
variables.put("contract", ClientValues.xmlValue(contractXmlString));

Invoice invoice = externalTask.getVariableTyped("invoice");
// modify invoice object
variables.put("invoice", ClientValue.objectValue(invoice)
    .serializationDataFormat("application/xml").create();

externalTaskService.complete(externalTask, variables);
```

## Configuration options
* The client can be configured with the fluent api of the [ExternalTaskClientBuilder](client/src/main/java/org/camunda/bpm/client/ExternalTaskClientBuilder.java). 
* The topic subscription can be configured with the fluent api of the [TopicSubscriptionBuilder](client/src/main/java/org/camunda/bpm/client/topic/TopicSubscriptionBuilder.java).

## Prerequisites
* Oracle Hotspot v1.8+ (JDK 8)
* Camunda BPM Platform 7.9.0+

## Maven coordinates
The following Maven coordinate needs to be added to the projects `pom.xml`:
```xml
<dependency>
  <groupId>org.camunda.bpm</groupId>
  <artifactId>camunda-external-task-client</artifactId>
  <version>${version}</version>
</dependency>
```

### JDK 9+ Support
If you want to use a JDK higher than 1.8, please add the following dependency to the projects `pom.xml`:
```xml
<dependency>
  <groupId>com.sun.xml.bind</groupId>
  <artifactId>jaxb-impl</artifactId>
  <version>2.2.4</version>
</dependency>
```

## License
The source files in this repository are made available under the [Apache License Version 2.0](./LICENSE).
