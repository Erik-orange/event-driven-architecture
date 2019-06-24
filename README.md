# event-driven-architecture

___

## Topology

#### Mediator Topology

The mediator topology consists of:
  * events
  * an event queue through which all events are processed
  * a mediator, (controller or orchestrator), which manages the order and channels in which an event is to be processed
  * services which perform business logic
  
#### Broker Topology

Rather than leverage a centralized mediator for orchestrating event and services, services subscribe to channels, execute their business logic, and then publish a new message to which other services subscribe. 

An advantage of this approach is that by removing the need for a mediator you’ve reduced complexity. 

The disadvantage is that coordination and enforcement of execution order are not handled.

___

ACID Transactions:
* **A**tomicity - Changes are made atomicatlly
* **C**onsistency – The state of the database is always consistent
* **I**solation – Even though transactions are executed concurrently it appears they are executed serially
* **D**urability – Once a transaction has committed it is not undone

___

In this architecture, a microservice publishes an event when something notable happens, such as when it updates a business entity. 

Other microservices subscribe to those events. 

When a microservice receives an event it can update its own business entities, which might lead to more events being published.

You can use events to implement business transactions that span multiple services. 

A transaction consists of a series of steps. 

Each step consists of a microservice updating a business entity and publishing an event that triggers the next step. 

___

#### APACHE KAFKA 

##### TERMINOLOGY:

* `KAFKA` - A distributed streaming system that runs on a cluster of computers.

* `PRODUCER` - An application that sends messages to the Kafka cluster for the broker to record.

* `CONSUMER` - An application that reads data from the Kafka server recorded by the broker.

* `BROKER` - A Kafka server. It acts as a message broker between producers and consumers.

* `CLUSTER` - A group of computers sharing workload for a common purpose.

* `TOPIC` - The unique name for a Kafka stream. A stream is defines as a continuous flow of data or a constant stream of messages.

* `PARTITION` - A part of a greater piece of a message that was broken down and distributed to multiple computers. Cannot be re-partitinoned. Size of partition set by us.

* `OFFSET` - A sequence ID given to messages as they arrive in a partition. This is immutable once assigned. No global scope, only local to partition.

* `CONSUMER GROUPS` - A group of consumers acting as a single logical unit.

* `STREAM PROCESSORS` - A third-party framework connected to a Kafka cluster for stream processing tasks. Read a constant stream of messages and then after processing the data they can send it back to the cluster or to other systems.

* `CONNECTORS` - Ready to use third-party tools to import data from databases into Kafka or to export data from Kafka into databases.

* `RECORD` - Consists of a key, a value, and a timestamp.

* `librdkafka` - A C library implementation of the Apache Kafka protocol, providing Producer, Consumer and Admin clients. It was designed with message delivery reliability and high performance in mind, current figures exceed 1 million msgs/second for the producer and 3 million msgs/second for the consumer.

* Apache Kafka is a distributed streaming platform:

  * Kafka is run as a `cluster` on one or more servers that can span multiple datacenters.
  
  * The Kafka cluster stores `streams` of `records` in categories called `topics`.

  * Each record consists of a `key`, a `value`, and a `timestamp`.


