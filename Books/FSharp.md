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
