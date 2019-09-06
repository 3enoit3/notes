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
  * **Decorator**: same implementation, but add new features
  * **Proxy**: same implementation, but control when/how to access it
  * **Flyweight**: merged implementations (intrisic)

* Same implementation:
  * **Adapter**: new interface
  * **Facade**: new interface which hides multiple objects behind a single one
  * **Composite**: new interface which uniformly handles composites and inviduals

### Behavioral
*Decouples sender and receiver*
* **Command**: the sender knows the receiver, but an external invoker decides when to process the request
* **Iterator**: the sender knows all receivers, but ignores their actual organization
* **Chain Of Responsibility**: the sender only knows the first receiver, which can stop or forward the request to its successor
* **Visitor**: the sender does not know receivers, but know how to process them
* **Observer**: the sender does not know receivers, but ? 
* **Mediator**: the sender and the receiver do not know each other

*Delegates behavior*
* **Strategy**/**Policy**: delegates algorithm to a class
* **Template Method**: delegates part of an algorithm to a child
* **State**: delegates event handling to a class

*Misc*
* **Memento**: captures the state of an object into an opaque class: only the object can access internals to restore its state
* **Interpreter**: implements a specialized language

## Seven Pernicious Kingdoms
https://cwe.mitre.org/data/definitions/700.html

# Software engineering
## Hierarchy
https://uvwx.github.io/hierarchy.html
* Fixations : (code style, best practices...)
* Requirements : (domain problem) what matters
* Models : (data structures, algorithms..) reduces the amount of code/time
* Notations : (domain languages..) integrates the model into the language, for even less amount of code/time
* Environments : (IDE to explore domain problem) integrates the problem domain into the user environment, to explore different implementations

## Strategy
https://www.csc.gov.sg/articles/how-to-build-good-software
* Start simple
* Seek Out Problems and Iterate
* Hire the Best Engineers You Can

### Refactoring
https://martinfowler.com/articles/is-quality-worth-cost.html
* Internal quality makes it easier to enhance software: it has value for the customers because the new features come quickly
* Even the best teams create cruft (technical debt) because we learn most about the problem as we're building the solution
* The difference is that the best teams refactor frequently so that they can remove cruft before it builds up enough to get in the way

## Environment
https://www.drmaciver.com/2016/10/some-things-that-might-help-you-write-better-software/
* Attitude
* Automated testing
  * Continuous integration
  * Local automated testing
  * Regression testing
  * Code coverage
  * Property-based testing
* Manual testing
* Version control
* Monorepos
* Static analysis
* Production error monitoring
* Assertions
* Code review
* Continuous delivery
* Auto formatting and style checking
* Documentation in the repository
* Plan to always have more capacity than work
* Projects should be structured as collections of libraries
* Ubiquitous working from home
* No long working hours
* Good work culture
* Good skill set mixing
