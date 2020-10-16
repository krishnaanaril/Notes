# F# for fun and profit

### Types

* Types cannot be declared inside functions.
* When creating new types it's better to stick with F# specific types rather  than using classes
* Types can be constructed and deconstructed
```f#
type A = int * int
let a = (1, 1) //construct
let (a1, a2) = a // deconstruct
```
* Class types has member keywords and has 'new' keyword for secondary constructors
* Stuct types are same as class but all members are abstract. Abstract emebers have colon and type signature rather than a concrete implementation.

### Tuples

* A particular instance of a tuple is a single object.
* The order of multiplication is importatn string * int is not equal to int * string.
* The comma is the critical symbol that define tuples, not the parentheses.
* When deconstructing tuples you must have the same number of elements, else use 'don't care' symbol (underscore) if not needed. 
```f#
let (_, b) = a
```

### Records

* Unlike tuples the order of the labels is not important.
* To avoid ambiguity use fully qualified names. e.g: `let p = {module.person.first="Alice", module.person.last="jones"}`
* Note that in F#, unlike some other functional languages, two types with exactly the same structural definition are not the same type. This is called a "nominal" type system, where two types are only equal if they have the same name, as opposed to a "structural" type system, where definitions with identical structures will be the same type regardless of what they are called.
