# Concurrency in C# - Cookbook

## Chapter 1 - Concurrency: An Overview
- **Concurrency** - Doing more than one thing at a time.
- **Multithreading** - A form of concurrency that uses multiple threads of execution.
- As soon as you type `new Thread()`, it’s over; your project already has legacy code.
- **Parallel Processing** - Doing lots of work by dividing it up among multiple threads that run concurrently.
- **Asynchronous Programming** - A form of concurrency that uses futures or callbacks to avoid unnecessary threads.
- A *future* (or *promise*) is a type that represents some operation that will complete in the future. Some modern future types in .NET are `Task` and `Task<TResult>`. 
- **Reactive Programming** - A declarative style of programming where the application reacts to events.
- Both benefits of asynchronous programming derive from the same underlying aspect: asynchronous programming frees up a thread. For GUI programs, asynchronous programming frees up the UI thread; For server applications, asynchronous programming frees up request threads.
- The `async` keyword is added to a method declaration, and performs a double purpose: it enables the `await` keyword within that method and it signals the compiler to 
 generate a state machine for that method, similar to how `yield return` works
 - ASP.NET Core does not have a **SynchronizationContext**. If you are on ASP.NET Core, it does not matter whether you use `ConfigureAwait(false)` or not.

> **Important**
>
> Read [ConfigureAwait FAQ](https://devblogs.microsoft.com/dotnet/configureawait-faq/)
- If you use `async`, it’s best to use `async` all the way
- There are two forms of parallelism: data parallelism and task parallelism.
- Data parallelism is when you have a bunch of data items to process, and the processing of each piece of data is mostly independent from the other
pieces. 
- Task parallelism is when you have a pool of work to do, and each piece of work is mostly independent from the other pieces. 
-  Parallel is more resource friendly than PLINQ; Parallel will play more nicely with other processes in the system, while PLINQ will (by default) attempt to spread itself over all CPUs.
- **TPL Dataflow** is useful when you have a sequence of processes that need to be applied to your data.
- Rx observables are generally better than dataflow blocks when doing anything related to timing. 
- Dataflow blocks are generally better than Rx observables when doing parallel processing. 
- There is almost no need for you to ever create a new thread yourself. The only time you should ever create a Thread instance is if you need an STA thread for COM interop.
- If you adopt a *functional* mindset, your concurrent designs will be less convoluted.
