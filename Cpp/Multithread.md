# Multithread
## Misc
* Spurious wakeup: a thread is awoken from its waiting state even though no thread signaled the condition variable 
  * Possible reason: system lost track of signals (ex. scheduler blackout) -> wakes up waiting thread by security

## Memory order
|Type|Operation|This thread|Other threads|
|-|-|-|-|
memory_order_relaxed|any|no synchronization/ordering constraints imposed on other rw, only this operation's atomicity is guaranteed|no |
memory_order_consume|load|no reads/writes dependent on the value currently loaded can be reordered **before this** load|Writes to data-dependent variables in other threads that release the same atomic variable are visible in the current thread (on most platforms, this affects compiler optimizations only)|
memory_order_acquire|load|no reads/writes can be reordered **before** this load|All writes in other threads that release the same atomic variable are visible in the current thread|
memory_order_release|store|no reads/writes can be reordered **after** this store|All writes in the current thread are visible in other threads that acquire the same atomic variable (see Release-Acquire ordering below) and writes that carry a dependency into the atomic variable become visible in other threads that consume the same atomic (see Release-Consume ordering below).|
memory_order_acq_rel|read-modify-write|no reads or writes can be reordered **before or after** this store|All writes in other threads that release the same atomic variable are visible before the modification and the modification is visible in other threads that acquire the same atomic variable.|
memory_order_seq_cst|all three||a single total order exists in which all threads observe all modifications in the same order|

## Use
* memory_order_relaxed: std::shared_ptr (note that decrementing the shared_ptr counters requires acquire-release synchronization with the destructor)
* 
## Reordering
* Compiler
* CPU
## Ordering
* **Happens-before**: A happens-before B if the execution behaves as-if all the memory effects of A are visible to the thread executing B _before_ executing it
* **Synchronize-with**: 
* **Compiler barrier**:

