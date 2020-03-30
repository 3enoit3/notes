# Programming
## [Revolution, Restoration and Revival](https://accu.org/var/uploads/journals/Overload148.pdf#page=4)
"most programming languages are rapidly converging on a quasi-object, quasi-functional, with generics, coroutines, threadpools and fibres model"
# Senior
## Checklist
https://littleblah.com/post/2019-09-01-senior-engineer-checklist/
## Improving
https://danluu.com/p95-skill/
## Experience
These are real cases I have experienced:
### Decisisions in big groups are difficult
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
