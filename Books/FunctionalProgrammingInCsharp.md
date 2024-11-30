# Functional Programming in C# - Enrico Buonanno

## Chapter 1

- What exactly is functional programming? At a very high level, it’s a programming style that
emphasizes functions while avoiding state mutation. 
- The reason you see both the functional and nonfunctional approaches in the framework is
historical: `List<T>.Sort` predates LINQ, which marked a decisive turn in a functional direction.
- There are several language constructs in C# that you can use to represent functions:
    - Methods
    - Delegates
    - Lambda expressions
    - Dictionaries
- If your function is short and you don’t need to reuse it elsewhere, lambdas offer the most
attractive notation.
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
- Unlike other side effects, I/O can’t be avoided, but you can still isolate the parts of your
application that perform I/O in order to reduce the footprint of impure code.

## Chapter 3 - Designing function signatures and types

- If you need to constrain the inputs of your functions, it’s usually better to define a custom type.
- A function is honest if its behavior can be predicted by its signature: it returns a value of the declared type; no throwing exceptions, and no null return values.
- **“honesty”** is an informal term, less technical and less rigorously defined than purity, but still useful.
- Indexers are, of course, just normal functions—the `[]` syntax is just sugar—so both indexers are
functions of type string → string, and both are *dishonest*.
- There’s an important distinction to make between total and partial functions:
    - Total functions are mappings that are defined for every element of the domain.
    - Partial functions are mappings that are defined for some, but not all, elements of the
    domain.
- Make your function signatures as specific as possible. This will make them easier to consume and less error-prone.
- Make your functions honest. An honest function always does what its signature says, and given an input of the expected type, it yields an output of the expected type—no `Exceptions`, no `nulls`.
- Use custom types rather than ad hoc validation code to constrain the input values of a
function, and use smart constructors to instantiate these types.
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