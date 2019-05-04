# Chapter 1: `this` or that?
* The *this* mechanism provides a more elegant way of implicitly "passing along" an object reference, leading to cleaner API design and easier re-use.
* To be clear, *this* does not, in any way, refer to a function's lexical scope. It is true that internally, scope is kind of like an object with properties for each of the available identifiers. 
* *this* is actually a binding that is made when a function is invoked, and what it references is determined entirely by the call-site where the function is called.
# Chapter 2
## Nothting but rules
1. Default binding, which depends on the call site of the function.
    * If strict mode is in effect, the global object is not eligible for the default binding, so the this is instead set to undefined.

**Note:** Intentionally mixing strict mode and non-strict mode together in your own code is generally frowned upon. Your entire program should probably either be Strict or non-Strict. However, sometimes you include a third-party library that has different Strict'ness than your own code, so care must be taken over these subtle compatibility details.

2. Implicit binding
3. Explicit binding

**Note:** With respect to this binding, call(..) and apply(..) are identical. They do behave differently with their additional parameters, but that's not something we care about presently.

4. Hard binding

**Note:** As of ES6, the hard-bound function produced by bind(..) has a .name property that derives from the original target function. For example: bar = foo.bind(..) should have a bar.name value of "bound foo", which is the function call name that should show up in a stack trace.

5. `new` binding
* Explicit binding takes precedence over implicit binding, which means you should ask first if explicit binding applies before checking for implicit binding. 

**Note:** `new` and `call/apply` cannot be used together, so new foo.call(obj1) is not allowed, to test new binding directly against explicit binding. But we can still use a hard binding to test the precedence of the two rules.

* If you pass null or undefined as a this binding parameter to call, apply, or bind, those values are effectively ignored, and instead the default binding rule applies to the invocation.

# Chapter 3: Objects
* Objects come in two forms: the declarative (literal) form, and the constructed form.
### Type

1. string
2. number
3. boolean
4. null
5. undefined
6. object

* `typeof null` returns object, which is an unfixed bug in js.

### Built-in Objects


1. String
2. Number
3. Boolean
4. Object
5. Function
6. Array
7. Date
8. RegExp
9. Error

* The language automatically coerces a "string" primitive to a String object when necessary, which means you almost never need to explicitly create the Object form. It is strongly preferred by the majority of the JS community to use the literal form for a value, where possible, rather than the constructed object form.

**Note:** ES6 adds a super reference, which is typically going to be used with class (see Appendix A). The way super behaves (static binding rather than late binding as this) gives further weight to the idea that a function which is super bound somewhere is more a "method" than "function". But again, these are just subtle semantic (and mechanical) nuances.

**Be careful:** If you try to add a property to an array, but the property name looks like a number, it will end up instead as a numeric index (thus modifying the array contents):

### Property Descriptors

* It includes 4 characteristics: `value`, `writable`, `enumerable`, and `configurable`.

**Note:** `writable:false` means a value cannot be changed, which is somewhat equivalent to if you defined a no-op setter. Actually, your no-op setter would need to throw a TypeError when called, to be truly conformant to `writable:false`.

**Be careful:** Changing configurable to false is a one-way action, and cannot be undone!. Also delete fails for `configurable:false` property

### Prevent Extensions
* If you want to prevent an object from having new properties added to it, but otherwise leave the rest of the object's properties alone, call `Object.preventExtensions(..)`:

### Seal 
* `Object.seal(..)` creates a "sealed" object, which means it takes an existing object and essentially calls Object.preventExtensions(..) on it, but also marks all its existing properties as `configurable:false`.

### Freeze
* `Object.freeze(..)` creates a frozen object, which means it takes an existing object and essentially calls `Object.seal(..)`on it, but it also marks all "data accessor" properties as `writable:false`, so that their values cannot be changed.

### Getters & Setters

* getter should have no paramter and setter should have only one parameter.

**Note:** As contrasted with iterating over an array's indices in a numerically ordered way (for loop or other iterators), the order of iteration over an object's properties is not guaranteed and may vary between different JS engines. Do not rely on any observed ordering for anything that requires consistency among environments, as any observed agreement is unreliable.

* Properties don't have to contain values -- they can be "accessor properties" as well, with getters/setters. They can also be either enumerable or not, which controls if they show up in for..in loop iterations, for instance.

* You can also iterate over the values in data structures (arrays, objects, etc) using the ES6 for..of syntax, which looks for either a built-in or custom @@iterator object consisting of a next() method to advance through the data values one at a time.

# Chapter 4: Mixing (Up) "Class" Objects
* JavaScript actually has classes? Plain and simple: **No.**

**Note:** Another thing that traditional class-oriented languages give you via `super` is a direct way for the constructor of a child class to reference the constructor of its parent class. This is largely true because with real classes, the constructor belongs to the class. However, in JS, it's the reverse -- it's actually more appropriate to think of the "class" belonging to the constructor (the Foo.prototype... type references). Since in JS the relationship between child and parent exists only between the two .prototype objects of the respective constructors, the constructors themselves are not directly related, and thus there's no simple way to relatively reference one from the other (see Appendix A for ES6 class which "solves" this with super).

* Explicit pseudo-polymorphism should be avoided wherever possible, because the cost outweighs the benefit in most respects.

# Chapter 5: Prototypes
* When attempting a property access on an object that doesn't have that property, the object's internal [[Prototype]] linkage defines where the [[Get]] operation (see Chapter 3) should look next. This cascading linkage from object to object essentially defines a "prototype chain" (somewhat similar to a nested scope chain) of objects to traverse for property resolution.
* For a variety of reasons, not the least of which is terminology precedent, "inheritance" (and "prototypal inheritance") and all the other OO terms just do not make sense when considering how JavaScript actually works (not just applied to our forced mental models).

* Instead, "delegation" is a more appropriate term, because these relationships are not copies but delegation links.
# Chapter 6: Behavior Delegation
**Note:** Some principles of class-oriented design are still very valid, so don't toss out everything you know (just most of it!). For example, encapsulation is quite powerful, and is compatible (though not as common) with delegation.

**Note:** Delegation is more properly used as an internal implementation detail rather than exposed directly in the API design. 
* You cannot create a cycle where two or more objects are mutually delegated (bi-directionally) to each other. 
* OLOO supports better the principle of separation of concerns, where creation and initialization are not necessarily conflated into the same operation.
# Appendix A: ES6 Class
* `class` does a very good job of pretending to fix the problems with the class/inheritance design pattern in JS. But it actually does the opposite: it hides many of the problems, and introduces other subtle but dangerous ones.