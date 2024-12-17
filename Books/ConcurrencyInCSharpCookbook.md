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

## Chapter 2 - Async Basics
- `Task.Delay` is a fine option for unit testing asynchronous code or for implementing retry logic. However, if you need to implement a timeout, a `CancellationToken` is usually a better choice.
- Pausing for a Period of Time
    - Q: You need to (asynchronously) wait for a period of time. 
    - A: The `Task` type has a static method `Delay` that returns a task that completes after the specified time.
- Returning Completed Tasks
    - Q: You need to implement a synchronous method with an asynchronous signature.
    - A: You can use `Task.FromResult` to create and return a new `Task<T>` that is already completed with the specified value.
-  Reporting Progress
    - Q: You need to respond to progress while an operation is executing.
    - A: Use the provided `IProgress<T>` and `Progress<T>` types.
- Waiting for a Set of Tasks to Complete
    - Q: You have several tasks and need to wait for them all to complete.
    - A: The framework provides a `Task.WhenAll` method for this purpose.
- Waiting for Any Task to Complete
    - Q: You have several tasks and need to respond to just one of them that’s completing
    - A: Use the `Task.WhenAny` method.
- If the other tasks aren’t canceled but are also never awaited, then they are abandoned. Abandoned tasks will run to completion, and their results will be ignored. Any exceptions from those abandoned tasks will also be ignored.
- Processing Tasks as They Complete
    - Q: You have a collection of tasks to await, and you want to do some processing on each task after it completes.
    - A: The easiest solution is to restructure the code by introducing a higher-level async method that handles awaiting the task and processing its result.
- Avoiding Context for Continuations
    - Q: When an async method resumes after an await, by default it will resume executing within the same context. This can cause performance problems if that context was a UI context and a large number of async methods are resuming on the UI context.
    - A: To avoid resuming on a context, await the result of `ConfigureAwait` and pass false for its `continueOnCapturedContext` parameter. (Not applicable for .NET core+. Needs further reading.)
- Handling Exceptions from async void Methods
    - Q: You have an async void method and need to handle exceptions propagated out of that method.
    - A: There is no good solution. If at all possible, change the method to return Task instead of void.
-  As a general rule, for your own application code, you should use `Task<T>` as a return type and not `ValueTask<T>`. Only consider using `ValueTask<T>` as a return type in your own application after profiling shows that you’d see a performance increase
- A `ValueTask` or` ValueTask<T>` may only be awaited once.
- Synchronously getting results from a `ValueTask` or `ValueTask<T>` may only be done once, after the `ValueTask` has completed, and that same `ValueTask` cannot be awaited or converted to a task.

## Chapter 3 - Asynchronous Streams
- `IAsyncEnumerable<T>` works just like an `IEnumerable<T>`, except that it asynchronously retrieves each next element.
- Creating Asynchronous Streams
    - Q: You need to return multiple values, and each value may require some asynchronous work. 
    - A: Returning multiple values from a method can be done with `yield return`, and asynchronous methods use `async` and `await`.
-  Consuming Asynchronous Streams
    - Q: You need to process the results of an asynchronous stream, also known as an asynchronous enumerable.
    - A: Consuming an asynchronous operation is done via `await`, and consuming an enumerable is usually done via `foreach`. Consuming an asynchronous enumerable is done by combining these two into `await foreach`. 
- `Observable` subscriptions must be synchronous, but `await foreach` permits natural asynchronous processing.
- Asynchronous streams are **pull-based**, so there’s no time-related operators like there are for observables. `Throttle` and `Sample` don’t make sense in this world, since the elements are pulled out of the asynchronous stream on demand.
- Asynchronous Streams and Cancellation
    - Q: You want a way to cancel asynchronous streams
    - A: Not all asynchronous streams require cancellation. It’s possible to simply stop enumerating when a condition is reached. Asynchronous streams support a `WithCancellation` extension method that you can use to attach a CancellationToken to a specific iteration of an asynchronous stream. With the `EnumeratorCancellation` parameter attribute in place, the compiler takes care of passing the token from `WithCancellation` to the token parameter marked by  `EnumeratorCancellation`, and the cancellation request now causes await foreach to raise an `OperationCanceledException` after it has processed the first few items.

## Chapter 4 - Parallel Basics
- Parallel Processing of Data
    - Q: You have a collection of data, and you need to perform the same operation on each element of the data. This operation is CPU-bound and may take some time.
    - A: The `Parallel` type contains a `ForEach` method specifically designed for this problem. 
- `Parallel.ForEach(matrices, (matrix, state) => {})`. This code uses `ParallelLoopState.Stop` to stop the loop, preventing any further invocations of the loop body.
- `Parallel.ForEach(matrices, new ParallelOptions { CancellationToken = token }, matrix => matrix.Rotate(degrees))` to cancel loop.
-  One difference between `Parallel` and `PLINQ` is that `PLINQ` assumes it can use all the cores on the computer, while `Parallel` will dynamically react to changing CPU conditions.
- Parallel Aggregation
    - Q: At the conclusion of a parallel operation, you need to aggregate the results.
    - A: If you’re already using the Parallel class, you may want to use its aggregation support. Otherwise, in most scenarios, the PLINQ support is more expressive and has shorter code.
- Parallel Invocation
    - Q: You have a number of methods to call in parallel, and these methods are (mostly) independent of one another.
    - A: The `Parallel` class contains a simple `Invoke` member that is designed for this scenario. 
- Dynamic Parallelism
    - Q: You have a more complex parallel situation where the structure and number of parallel tasks depend on information known only at runtime.
    - A: When you need dynamic parallelism, it’s easiest to use the `Task` type directly.

- Using Task for parallel processing is completely different than using Task for asynchronous processing
- The Task type serves two purposes in concurrent programming: it can be a parallel task or an asynchronous task.
- Asynchronous tasks should not use AttachedToParent, but they can form an implicit kind of parent/child relationship by awaiting another task.
- The Parallel class is good for many scenarios, but PLINQ code is simpler when doing aggregation or transforming one sequence to another.
- Bear in mind that the Parallel class is more friendly to other processes on the system than PLINQ; this is especially a consideration if the parallel processing is done on a server machine.

## Chapter 5 - DataFlow Basics
