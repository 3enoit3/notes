# Programming
## [Revolution, Restoration and Revival](https://accu.org/var/uploads/journals/Overload148.pdf#page=4)
"most programming languages are rapidly converging on a quasi-object, quasi-functional, with generics, coroutines, threadpools and fibres model"
# Senior
## Checklist
https://littleblah.com/post/2019-09-01-senior-engineer-checklist/
## Improving
https://danluu.com/p95-skill/
# Experience
## Decisisions in big groups are difficult
* high latency
* first attempt to solve it: put 10 seniors in a meeting room for an hour -> no clear lead, no decision
* second attempt to solve it: put 4 seniors in a meeting room for a day -> ?
## Abtraction is losing information
* ex:
  * a main state machine could drive an error management state machine using a unique id pointing to a general state machine interface: the two state machines are isolated, but it is not possible to use fine-grain error management.
## Interface is more important than implementation
* interface is leaking everywhere
* implementation can be easily changed / improved
* ex:
  * the structure of communication protocol is not important at the beginning, but if it is not hidden behind a simple interface, it becomes very difficult to uniformize it later (but it is not as simple either, because abstraction is losing information - cf previous)
## Responsibility over reuse
* ex:
  * a main service and an alert service work together to raise alerts; if the main service gives functional information for the alert service to decide if an alert should be raised, the alert service will have a tendency to pull more private data out of the main service when more complex scenario will come.
