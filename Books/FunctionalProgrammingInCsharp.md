# Functional Programming in C# - Enrico Buonanno

## Chapter 1

- What exactly is functional programming? At a very high level, it’s a programming style that emphasizes functions while avoiding state mutation. 
- The reason you see both the functional and nonfunctional approaches in the framework is historical: `List<T>.Sort` predates LINQ, which marked a decisive turn in a functional direction.
- There are several language constructs in C# that you can use to represent functions:
    - Methods
    - Delegates
    - Lambda expressions
    - Dictionaries
- If your function is short and you don’t need to reuse it elsewhere, lambdas offer the most attractive notation.
- Use function pointers in LINQ clauses for better readablility. 
- HOFs also have some drawbacks:
    - You’ve increased stack use. There’s a performance impact, but it’s negligible.
    - Debugging the application will be a bit more complex because of the callbacks.
- Use **HOFs** when appropriate, but be mindful of readability: use short lambdas, clear naming, and meaningful indentation.

## Chapter 2 - Function Purity

- PLINQ is an implementation of LINQ to Objects that works in parallel.
- Side effects include state mutation, throwing exceptions, and I/O.
- Static methods can cause problems if they do either of the following:
    - Act on mutable static fields
    - Perform I/O
- When a function is pure, there’s no downside to making it static. As a general guideline,
    - Make pure functions static.
    - Avoid mutable static fields.
    - Avoid direct calls to static methods that perform I/O.
- Unlike other side effects, I/O can’t be avoided, but you can still isolate the parts of your application that perform I/O in order to reduce the footprint of impure code.

## Chapter 3 - Designing function signatures and types

- If you need to constrain the inputs of your functions, it’s usually better to define a custom type.
- A function is honest if its behavior can be predicted by its signature: it returns a value of the declared type; no throwing exceptions, and no null return values.
- **“honesty”** is an informal term, less technical and less rigorously defined than purity, but still useful.
- Indexers are, of course, just normal functions—the `[]` syntax is just sugar—so both indexers are functions of type string → string, and both are *dishonest*.
- There’s an important distinction to make between total and partial functions:
    - Total functions are mappings that are defined for every element of the domain.
    - Partial functions are mappings that are defined for some, but not all, elements of the
    domain.
- Make your function signatures as specific as possible. This will make them easier to consume and less error-prone.
- Make your functions honest. An honest function always does what its signature says, and given an input of the expected type, it yields an output of the expected type—no `Exceptions`, no `nulls`.
- Use custom types rather than ad hoc validation code to constrain the input values of a function, and use smart constructors to instantiate these types.
- Use the `Option` type to express the possible absence of a value. An `Option` can be in one of
two states:
    - `None`, indicating the absence of a value
    - `Some`, a simple container wrapping a a non-null value
- To execute code conditionally, depending on the state of an Option, use Match with the
functions you’d like to evaluate in the `None` and `Some` cases.

## Chapter 4 - Patterns in functional programming

- In FP, a type for which such a `Map` function is defined is called a `functor`.
- Similarly, `monads` are types for which a `Bind` function is defined.
- Structures like `Option<T>` and `IEnumerable<T>` can be seen as containers or abstractions, allowing you to work more effectively with the underlying values of type T.
- You can distinguish between regular values, say, T, and elevated values, like `Option<T>` or `IEnumerable<T>`.
- Some of the core functions of FP allow you to work effectively with elevated values:
    - `Return` is a function that takes a regular value and lifts it into an elevated value.
    - `Map` applies a function to the inner value(s) of a structure, and returns a new structure wrapping the result.
    - `ForEach` is a side-effecting variant of Map that takes an action, which it performs for each of the container’s inner values.
    - `Bind` maps an Option-returning function onto an Option and flattens the result to avoid producing a nested Option—and similarly for IEnumerable and other structures.
    - `Where` filters the inner value(s) of a structure according to a given predicate.
- Types for which `Map` is defined are called `functors`. Types for which `Return` and `Bind` are defined are called `monads`.

## Chapter 5 - Designing programs with function composition

- Function composition means combining two or more functions into a new function, and it’s widely used in FP.
- In C#, the extension method syntax allows you to use function composition by chaining methods.
- Functions lend themselves to being composed if they are pure, chainable, and shape-preserving.
- Workflows are sequences of operations that can be effectively expressed in your programs through function pipelines: one function for each step of the workflow, with the output of each function fed into the next.
- The LINQ library has a rich set of easily composable functions to work with IEnumerables, and you can use it as inspiration to write your own APIs.
- Functional code prefers expressions over statements, unlike imperative code.
- Relying on expressions leads to your code becoming more declarative, and hence more readable.

## Chapter 6 -  Functional error handling

- Use `Either` to represent the result of an operation with two different possible outcomes, typically success or failure. An `Either` can be in one of two states:
    - `Left` indicates failure and contains error information for an unsuccessful operation.
    - `Right` indicates success and contains the result of a successful operation.
- Interact with `Either` using the equivalents of the core functions already seen with Option:
    - `Map` and `Bind` apply the mapped/bound function if the `Either` is in the Right state; otherwise they just pass along the Left value.
    - `Match` works similarly to how it does with Option, allowing you to handle the Right and Left cases differently.
    - `Where` is not readily applicable, so `Bind` should be used in its stead for filtering, while providing a suitable Left value.
- `Either` is particularly useful for combining several validation functions with Bind, or, more generally, for combining several operations, each of which can fail.
- Because `Either` is rather abstract, and because of the syntactic overhead of its two generic arguments, in practice it’s better to use a particularized version of `Either`, such as
Validation and Exceptional.
- When working with functors and monads, prefer using functions that stay within the abstraction, like `Map` and `Bind`. Use the downward-crossing `Match` function as little or as late
as possible.

## Chapter 7 - Structuring an application with function

- Partial application is always about going from general to specific. It allows you to define very general functions and then fine tune their behavior by giving them arguments.
- **Partial application** means giving a function its arguments piecemeal, effectively creating a more specialized function with each argument given.
- **Currying** means changing the signature of a function so that it will take its arguments one at a time.
- Partial application enables you to write highly general functions by parameterizing their behavior, and then supplying arguments to obtain increasingly specialized functions.
- The order of arguments matters: you give the leftmost argument first, so that a function should declare its arguments from general to specific.
- When working with multi-argument functions in C#, method resolution can be problematic and lead to syntactic overhead. This can be overcome by relying on Funcs rather than on
methods.
- You can inject the dependencies required by your functions by declaring them as arguments. This allows you to compose your application entirely of functions, without
compromising on the separation of concerns, decoupling, and testability.

## Chapter 8 - Working effectively with multi-argument functions

- A monad is a type, `M`, for which the following functions are defined:
    - `Return`, which takes a regular value of type `T` and lifts it into a monadic value of type `M<T>`
    - `Bind`, which takes a monadic value, `m`, and a world-crossing function, `f`, and “extracts” from `m` its inner value `t` and applies `f` to it
- `Return` and `Bind` should have the following three properties:
    1. Right identity
    2. Left identity
    3. Associativity
- The `Apply` function can be used to perform function application in an elevated world, such as the world of Option.
- Multi-argument functions can be lifted into an elevated world with Return, and then arguments can be supplied with Apply.
- Types for which Apply can be defined are called applicatives. Applicatives are more powerful than functors, but less powerful than monads.
- Because monads are more powerful, you can also use nested calls to Bind to perform function application in an elevated world.
- LINQ provides a lightweight syntax for working with monads that reads better than nesting calls to Bind.
- To use LINQ with a custom type, you must implement the LINQ query pattern, particularly providing implementations of Select and SelectMany with appropriate signatures.
- For several monads, Bind has short-circuiting behavior (the given function won’t be applied in some cases), but Apply doesn’t (it’s not given a function, but rather an elevated value). For this reason, you can sometimes embed desirable behavior into applicatives, such as collecting validation errors in the case of Validation.
- FsCheck is a framework for property-based testing. It allows you to run a test with a large number of randomly generated inputs, giving high confidence that the test’s assertions hold for any input

## Chapter 9 - Thinking about data functionally

- The FP paradigm discourages state mutation, preventing several drawbacks associated with state mutation, such as lack of thread safety, coupling, and impurity.
- Things that don’t change are represented with immutable objects.
- In FP, things that change are also represented with immutable objects; these immutable snapshots represent an entity’s state at a given point. Change is represented by creating a new snapshot with the desired changes.
- Enforcing immutability in C# is doable, but laborious; using immutability by convention, or modeling domain objects in F# are alternatives worth considering.
- Like objects, collections should also be immutable, so that existing collections are never altered, but rather new collections are created with the desired changes.
- Immutable collections can be safe as well as efficient, because an updated version shares much of its structure with the original collection without affecting it.

## Chapter 10 - Event sourcing: a functional approach to persistence

- The traditional functions of a relational DB are the CRUD operations: create, read, update, and delete. The functional approach to data storage is CRA: create, read, append.
- Thinking functionally about data also encompasses storage. Instead of mutating stored data, consider the database as a big immutable collection: you can append new data, but never overwrite existing data.
- There are two main approaches to immutable storage:
    - *Event-based*—The DB is an ever-growing collection of events.
    - *Assertion-based*—The DB is an ever-growing collection of facts.
- Event sourcing means persisting event data as events occur. The state of an entity need not be stored, because it can always be computed as the “sum” of all events that affected the entity.
- An event-sourced system naturally separates the concerns of reading and writing data, enabling a CQRS architecture that separates between
    - The command side, where commands are received, validated, and turned into events that are persisted and published.
    - The query side, where events are combined to create view models, which are served to clients and, optionally, cached for better performance.
- Event-sourced systems have several main components:
    - *Commands*—Simple, immutable data objects encapsulating a request from a client program.
    - *Events*—Simple, immutable data objects capturing what happened.
    - *States*—Data objects representing the state of an entity at a certain point in time.
    - *State transitions*—Functions that take a state and an event, and produce a new state.
    - *View models*—Data objects for populating views. They’re computed from events.
    - *Event handlers*—These subscribe to events to perform business logic (on the command side) or to update view models (on the query side).

## Chapter 11 - Lazy computations, continuations, and the beauty of monadic composition
-  C# is a language with strict or eager evaluation—expressions are evaluated as soon as they’re bound to a variable. Although strict evaluation is more common, there are languages—notably Haskell—that use lazy evaluation, so that expressions are evaluated only as needed.
- If you’re not sure whether a value will be required, and it may be expensive to compute it, pass the value lazily by wrapping it in a function that will compute the value.
- Types for which two instances can always be combined into one are called monoids.
- Laziness means deferring a computation until its result is needed. It’s especially useful when the result may not be required in the end.
- Lazy computations can be composed to create more complex computations that can then  be triggered as needed.
- When dealing with an exception-based API, you can use the `Try` delegate type. The Run function safely executes the code in the `Try` and returns the result wrapped in an `Exceptional`.
- HOFs in the form `(T → R) → R` (that is, functions that take a callback or continuation) can also be composed monadically, enabling you to use flat LINQ expressions rather than deeply nested callbacks.

## Chapter 12 - Stateful programs and stateful computations

- *Stateful computations* are functions that take a state (as well as, potentially, other arguments), and return a new state (along with, potentially, a return value). They’re also called state transitions.
- When writing stateful programs, you can avoid changing state as a side effect by always passing the state explicitly as part of a function’s input and output.
- Stateful computations are functions in the form `S → (T, S)`. That is, they take some state and return a value as well as an updated state.
- Stateful computations can be composed monadically, to reduce the syntactic burden of passing the state from one computation to the next.

## Chapter 13 - Working with asynchronous computations
- `Traverse` is one of the slightly more esoteric core functions in FP, and it allows you to work with lists of elevated values. 
- Task<T> represents a computation that will asynchronously deliver a T.
- Tasks should be used whenever the underlying operation may have significant latency, such as most I/O operations.
- Task-returning functions can be composed with `Map`, `Bind`, and several other combinators to specify error handling or multiple retries.
- If Tasks are independent, they can be run in parallel. You can use Task as an applicative, and providing several Tasks with Apply runs them in parallel.
- If you have two monads, A and B, you may like to stack them up in values like `A<B<T>>`, to combine the effects of each monad.
- Traverse can be used to invert the order of monads in the stack. 
- Implementing the query pattern for such a stack allows you to combine As, Bs, and` A<B<>>`s with relative ease. Still, stacked monads tend to be cumbersome, so use them sparingly

## Others

- Use higher-order functions with LINQ and avoid writing your own for-loops.Try to avoid unnecessary repetition. For many things, there are generic algorithms. Use LINQ and other Algorithms to create powerful abstractions. If there is not an algorithm available, try to be generic and write your own algorithms.

| Task | Linq |
|------|------|
| Projection |	Select, SelectMany |
| Aggregation |	Aggregate, Sum, Min, Max, Average, Count |
| Restriction |	Where |
| Existence |	Any, All, Contains, Distinct |
| Set Operations |	Contains, Distinct, Union, Intersect, Except |
| Sorting |	OrderBy, ThenBy, OrderByDescending, ThenByDescending |
| Paging |	First, Last, Single, Skip, Take, SkipWhile, TakeWhile |
| String | Formating	string.Format() or use $"" (String interpolation) |