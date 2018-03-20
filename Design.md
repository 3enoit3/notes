# Software design
## Rules
### SOLID
### Law of Demeter
Principle of least knowledge: only talk to your immediate friends.

## GOF Patterns
### Creational
*Delegates creations*
* **Factory Method**: delegates creations to a child
* **Abstract Factory**: delegates family creations to a class: *one method per objet*
* **Builder**: delegates complex creations to a class: *one method for several objects*
* **Prototype**: delegates creations to an object of the same class: *clone()*
* **Singleton**: delegates the single creation to a class: *instance()*

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

* **Chain Of Responsibility**: delegates commands to a chain of processing objects.
* **Command**: creates objects which encapsulate actions and parameters.
* **Interpreter**: implements a specialized language.
* **Iterator**: accesses the elements of an object sequentially without exposing its underlying representation.
* **Mediator**: allows loose coupling between classes by being the only class that has detailed knowledge of their methods.
* **Memento**: provides the ability to restore an object to its previous state (undo).
* **Observer**: is a publish/subscribe pattern which allows a number of observer objects to see an event.
* **State**: allows an object to alter its behavior when its internal state changes.
* **Strategy**: allows one of a family of algorithms to be selected on-the-fly at runtime.
* **Template Method**: defines the skeleton of an algorithm as an abstract class, allowing its subclasses to provide concrete behavior.
* **Visitor**: separates an algorithm from an object structure by moving the hierarchy of methods into one object.
