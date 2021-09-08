# Multithread
## Misc
* Spurious wakeup: a thread is awoken from its waiting state even though no thread signaled the condition variable 
  * Possible reason: system lost track of signals (ex. scheduler blackout) -> wakes up waiting thread by security
* Lost wakeup : a thread is waiting for a event which has already happened
  * Possible reason: condition_variable wait() without predicate
* Race condition
  * https://github.com/google/sanitizers/wiki/ThreadSanitizerPopularDataRaces

## Tools
```c++
// Atomics on Windows
int i;
InterlockedIncrement(&i);
InterlockedDecrement(&i);

// Mutexes
// shared across threads
std::mutex m; // cannot be moved/copied
m.lock();
m.unlock();

// Locks
// local to a thread, to protect a (small) section of code 
std::lock_guard<std::mutex> guard(m); // cannot be unlocked/moved/copied
std::unique_lock<std::mutex> lock(m); // can be unlocked/moved, cannot be copied

// Condition variables
// shared across threads, to wait for an event
std::condition_variable c;
bool ready; // ! needed to prevent lost/spurious wakeup: https://www.modernescpp.com/index.php/c-core-guidelines-be-aware-of-the-traps-of-condition-variables
{ // Consumer
  std::unique_lock<std::mutex> lock(m);
  condVar.wait(lock, []{ return ready; });
  // read shared data protected by m thanks to wait
}
{ // Producer
  {
    std::lock_guard<std::mutex> lck(mutex_);
    // write shared data
    ready = true; // no need for a lock if ready is atomic<bool>
  }
  cond.notify_one(); // wake up consumer
}

// Call once
boost::once_flag o = BOOST_ONCE_INIT;
boost::call_once(&init, o);

// Future
// one-time channel shared across threads, to send a single data
// can be implemented with a condition_variable (https://mciantyre.github.io/post/2017-09-20-cpp-promises-futures/)
std::promise<int> p; // "pull end" of the channel: it "promises" the consumer it will be fulfilled
std::future<int> f = p.get_future(); // "push end" of the channel: the producer will use it to fulfill the promise, can be moved, cannot be copied
{ // Consumer
  int i = f.get(); // wait
}
{ // Producer
  p.set(1); // fullfill
}

std::shared_future<int> sf; // can be copied (multiple consumers)
```

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
* Compiler: optimization if no change for the external world
* CPU: out of order
## Ordering
* **Happens-before**: A happens-before B if the execution behaves as-if all the memory effects of A are visible to the thread executing B _before_ executing it
* **Synchronize-with**: 
* **Compiler barrier**:

# Threads
## Interruption
```c++
another_thread.interrupt(); // non blocking
another_thread.join();
```
* The interrupted thread will throw a **boost::thread_interrupted** exception when reaching the next:
  * boost::thread: join(), timed_join()
  * boost::this_thread: sleep(), interruption_point()
  * boost::condition_variable/condition_variable_any: wait(), timed_wait()
* It can be temporarily deactivated (*ex: to protect exception in destructors*):
```c++
boost::this_thread::disable_interruption di; // deactivate interruptions
... // no exception on interruption points
boost::this_thread::restore_interruption ri(di); // reactivate interruptions
```
# Fibers
https://en.wikipedia.org/wiki/Fiber_(computer_science)
# Coroutines

# Atomics
https://medium.com/@tylerneely/fear-and-loathing-in-lock-free-programming-7158b1cdd50c

# Mutexes
https://accu.org/index.php/journals/1324
http://lucteo.ro/2018/11/18/look-ma-no-locks/

# Semaphore
N resources are available: there cannot be more than N actors accessing these resources.<br>
A semaphore is an extension of a simple mutex, as a mutex can be seen as a semaphore with N=1
