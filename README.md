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
