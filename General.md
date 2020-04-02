# Software engineering
## Strategy
https://www.csc.gov.sg/articles/how-to-build-good-software
* Start simple
* Seek Out Problems and Iterate
* Hire the Best Engineers You Can

## Refactoring
https://martinfowler.com/articles/is-quality-worth-cost.html
* Internal quality makes it easier to enhance software: it has value for the customers because the new features come quickly
* Even the best teams create cruft (technical debt) because we learn most about the problem as we're building the solution
* The difference is that the best teams refactor frequently so that they can remove cruft before it builds up enough to get in the way

## Hierarchy
https://uvwx.github.io/hierarchy.html
* Fixations : (code style, best practices...)
* Requirements : (domain problem) what matters
* Models : (data structures, algorithms..) reduces the amount of code/time
* Notations : (domain languages..) integrates the model into the language, for even less amount of code/time
* Environments : (IDE to explore domain problem) integrates the problem domain into the user environment, to explore different implementations

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

## [Revolution, Restoration and Revival](https://accu.org/var/uploads/journals/Overload148.pdf#page=4)
"most programming languages are rapidly converging on a quasi-object, quasi-functional, with generics, coroutines, threadpools and fibres model"

# Senior
## Checklist
https://littleblah.com/post/2019-09-01-senior-engineer-checklist/
## Improving
https://danluu.com/p95-skill/
## My experience
Real cases I have experienced.
### Decisions in big groups are difficult
* high latency
* first attempt to solve it: put 10 seniors in a meeting room for an hour -> no clear lead, no decision
* second attempt to solve it: put 4 seniors in a meeting room for a day -> ?
### Abstracting is losing information
* ex:
  * several state machines can communicate through a generic event queue, hiding the dependencies between state machines: this is easy to test in isolation, but some scenario are simpler to solve if state machines know each other.
### Interface is more important than implementation
* interface is leaking everywhere
* implementation can be easily changed / improved
* ex:
  * the communication protocol is not important at the beginning of a project, but if it is not hidden behind a simple interface, it becomes very difficult to uniformize it later (but early hidding is not as simple either, because abstraction is losing information - cf previous)
### Single responsibility is more important than reusing
* ex:
  * a main service and an alert service work together to raise alerts; if the main service gives functional information for the alert service to decide if an alert should be raised, the alert service will have a tendency to pull more private data out of the main service when more complex scenario will come.
