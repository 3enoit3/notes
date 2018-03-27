# Software design
## Rules
### SOLID
### Law of Demeter
Principle of least knowledge: only talk to your immediate friends.

## GOF Patterns
### Creational
*Delegates creations*
* **Factory Method**: delegates creations to a child
* **Abstract Factory**: delegates family creations to a class: **one method per objet**
* **Builder**: delegates complex creations to a class: **one method for several objects**
* **Prototype**: delegates creations to an object of the same class: **clone()**
* **Singleton**: delegates the single creation to a class: **instance()**

### Structural
*Decouples interface and implementation*
* Same interface:
  * **Bridge**: new implementation
  * **Decorator**: same implementation but add new features
  * **Proxy**: same implementation but control when/how to access it
  * **Flyweight**: merged implementations (intrisic)

* Same implementation:
  * **Adapter**: new interface
  * **Facade**: new interface which hides multiple objects behind a single one
  * **Composite**: new interface which uniformly handles composites and inviduals

### Behavioral
*Decouples sender and receiver*
* **Iterator**: the sender knows all receivers but ignores their actual organization
* **Visitor**: the sender does not know receivers but know how to process them
* **Command**: the sender knows the receiver, but an external invoker decides when to process the request
* **Chain Of Responsibility**: the sender only knows the first receiver, which can stop or forward the request to a successor
* **Observer**: the sender does not know the receivers
* **Mediator**: the sender and the receiver do not know each other

*Delegates behavior*
* **Strategy**/**Policy**: delegates algorithm to a class
* **Template Method**: delegates part of an algorithm to a child
* **State**: delegates event handling to a class

*Misc*
* **Memento**: captures the state of an object into an opaque class: only the object can access internals to restore its state
* **Interpreter**: implements a specialized language
