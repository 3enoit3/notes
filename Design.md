# Software design
## Rules
### SOLID
### Law of Demeter
Principle of least knowledge: only talk to your immediate friends.

## GOF Patterns
### Creational
*Delegate creations*
* **Factory Method**: delegate creations to a child
* **Abstract Factory**: delegate family creations to a class: *one method per objet*
* **Builder**: delegate complex creations to a class: *one method for several objects*
* **Prototype**: delegate creations to an object of the same class: *clone()*
* **Singleton**: delegate the single creation to a class: *instance()*

### Structural
*Decouple interface and implementation*
* **Bridge**: keep interface, change implementation
* **Decorator**: keep interface, keep implementation but add new features
* **Proxy**: keep interface, keep implementation but control when/how to access it
* **Flyweight**: keep interface, merge common implementations (intrisic)
<br>

* **Adapter**: keep implementation, change interface
* **Facade**: keep implementation, change interface by hiding multiple objects behind a single one
* **Composite**: keep implementation, change interface to uniformly handle composites and inviduals

### Behavioral
