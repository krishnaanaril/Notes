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
-  Linking Blocks
    - Q: You need to link dataflow blocks to one another to create a mesh.
    - A: Many of the useful TPL Dataflow methods are actually extension methods. The `LinkTo` extension method provides an easy way to link dataflow blocks together.
    ```C#    
    var options = new DataflowLinkOptions { PropagateCompletion = true };
    multiplyBlock.LinkTo(subtractBlock, options);
    ```
-  Propagating Errors
    - Q: You need a way to respond to errors that can happen in your dataflow mesh.
    - When you propagate completion using the `PropagateCompletion` link option, errors are also propagated. However, the exception is passed to the next block wrapped in an `AggregateException`
- Unlinking Blocks
    - Q: During processing, you need to dynamically change the structure of your dataflow.
    - A: You can link or unlink dataflow blocks at any time; data can be freely passing through the mesh and it’s still safe to link or unlink at any time. Both linking and unlinking are fully threadsafe.
- Throttling Blocks
    - Q: You have a fork scenario in your dataflow mesh and want the data to flow in a load-balancing way.
    - A: This problem can be fixed by throttling the target blocks using the `BoundedCapacity` block option. By default, `BoundedCapacity` is set to `DataflowBlockOptions.Unbounded`, which causes the first target block to buffer all the data even if it isn’t ready to process it yet.
- Parallel Processing with Dataflow Blocks
    - Q: You want to perform some parallel processing within your dataflow mesh.
    - A: You can instruct that block to operate in parallel on its input data by setting the `MaxDegreeOfParallelism` option. By default, this option is set to 1, so each dataflow block will only process one piece of data at a time.
-  `DataflowBlock.Encapsulate` will create a single block out of the two endpoints.

## Chapter 6 - System.Reactive Basics
- Converting .NET Events
    - Q: You have an event that you need to treat as a System.Reactive input stream, producing some data via OnNext each time the event is raised.
    - A: Most .NET framework events are compatible with FromEventPattern, but if you have events that don’t follow the common pattern, you can use FromEvent instead.
- The most common uses for the `ObserveOn` operator are moving on or off the UI thread, but schedulers are also useful in other scenarios. A more advanced scenario where schedulers are useful is faking the passage of time when unit testing
- `ObserveOn` controls the context for the observable notifications. This is not to be confused with `SubscribeOn`, which controls the context for the code that adds and removes the event handlers.
- `System.Reactive` provides a pair of operators that group incoming sequences: `Buffer` and `Window`. `Buffer` will hold on to the incoming events until the group is complete, at which time it forwards them all at once as a collection of events. `Window` will logically group the incoming events but will pass them along as they arrive. The return type of `Buffer` is `IObservable<IList<T>>` (an event stream of collections); the return type of Window is `IObservable<IObservable<T>>` (an event stream of event streams).
- Taming Event Streams with Throttling and Sampling
    - Q: A common problem with writing reactive code is when the events come in too quickly. A fast-moving stream of events can overwhelm your program’s processing.
    - A: `System.Reactive` provides operators specifically for dealing with a flood of event data. The `Throttle` and `Sample` operators give us two different ways to tame fast input events.

## Chapter 7 - Testing
- Two main advantages of unit testing:
    - Better understanding of the code
    - Greater confidence to make changes
- Testing error handling is just as important as testing the successful scenarios.
- It’s better to test for an exception thrown at a specific point rather than testing for an exception at any time during the test. Instead of `ExpectedException`, use `ThrowsAsync` (or its equivalent in your unit test framework)
-  Rx introduced a concept called a *scheduler*, and every Rx operator that deals with time is implemented using this abstract scheduler.
- `TestScheduler` is in a separate NuGet package from the rest of `System.Reactive`; you’ll need to install the `Microsoft.Reactive.Testing` NuGet package. `TestScheduler` gives you powerful control over (virtual) time.
- `TestScheduler` also has `AdvanceTo` and `AdvanceBy` methods, which enable you to gradually step through virtual time.

## Chapter 8 - Interop
- For new code, always use `HttpClient`. Only use `WebClient` if you’re working with legacy code.

## Chapter 9 - Collections
-  Immutable collections follow a pattern where they return an updated collection; the original collection reference is unchanged. This means that once you have a 
 reference to a particular immutable collection instance, it’ll never change.
 - Even though immutable collections are threadsafe, references to immutable collections are not threadsafe. A variable that refers to an immutable collection needs the same synchronization protections as any other variable.
- The immutable list is internally organized as a binary tree so that immutable list instances may maximize the amount of memory they share with other instances.
- One important note about the sorted set is that its indexing is O(log N), not O(1), just like ImmutableList<T>. This means that the same caveat applies in this situation: you should use foreach instead of for whenever possible with an `ImmutableSortedSet<T>`.
- The `ConcurrentDictionary<TKey, TValue>` type in the .NET framework is a true gem of a data structure. It’s threadsafe, using a mixture of fine-grained locks and lock-free techniques to ensure fast access in the vast majority of scenarios.
- You need a conduit to pass messages or data from one thread to another. The .NET type `BlockingCollection<T>` was designed to be this kind of conduit. By default, `BlockingCollection<T>` is a blocking queue, providing first-in, first-out behavior.
- A lot of the time, using TPL Dataflow is simpler than building your own conduits and background threads.
- Channels are a modern library for asynchronous producer/consumer collections, with a nice emphasis on high performance for high-volume scenarios.
- Channels are the easiest way to apply sampling to input items. One common example is to always take the latest n items, discarding the oldest items once the queue is full.
    ```csharp
    Channel<int> queue = Channel.CreateBounded<int>(
    new BoundedChannelOptions(1)
    {
    FullMode = BoundedChannelFullMode.DropOldest,
    });
    ChannelWriter<int> writer = queue.Writer;
    ```

## Chapter 10 - Cancellation
- Cancellation is treated as a special kind of error. The convention is that canceled code will throw an exception of type `OperationCanceledException` (or a derived type, such as `TaskCanceledException`). This way the calling code knows that the cancellation was observed.
- To execute code with a timeout, use `CancellationTokenSource` and `CancelAfter` (or the constructor). There are other ways to do the same thing, but using the existing cancellation system is the easiest and most efficient option.
- Remember that the code to be canceled needs to observe the cancellation token; it isn’t possible to easily cancel un-cancelable code.
- The easiest way to support cancellation is to pass the `CancellationToken` through to the parallel code. `Parallel` methods support this by taking a `ParallelOptions` instance.
- The System.Reactive library has a notion of a *subscription* to an observable stream. Your code can dispose of the subscription to unsubscribe from the stream. In many cases, this is sufficient to logically cancel the stream.
- Each block in a dataflow mesh supports cancellation as a part of its `DataflowBlockOptions`.
- The `CreateLinkedTokenSource` method can take any number of cancellation tokens as parameters. This enables you to create a single combined token from which you can implement your logical cancellation.

## Chapter 11 - Functional-Friendly OOP
- The async keyword can only be applied to methods with implementations; it isn’t possible to apply it to abstract methods or interface methods (unless they have default implementations).
- If you want to do some async work in the construtor, the bettern pattern is to create a `static` method that does the initalization and make the constructor `private`. Constructors cannot be async, nor can they use the await keyword. 
- One of the important questions to ask yourself is whether reading the property should start a new 
 asynchronous operation; if the answer is yes, then use an asynchronous method instead of a property.
