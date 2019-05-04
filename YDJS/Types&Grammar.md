# Chpater 1: Types
### Built-in types

* null
* undefined
* boolean
* number
* string
* object
* symbol -- added in ES6!

**Note:** All of these types except object are called "primitives".

**Note:** If you're defining a "polyfill" for a feature if it doesn't already exist, you probably want to avoid using `var`
# Chpater 2: Values
**Warning:** Using delete on an `array` value will remove that slot from the array, but even if you remove the final element, it does not update the length property, so be careful! 
### Numbers
* Like most modern languages, including practically all scripting languages, the implementation of JavaScript's numbers is based on the "IEEE 754" standard, often called "floating-point." JavaScript specifically uses the "double precision" format (aka "64-bit binary") of the standard.
### Void Operator
* The expression void ___ "voids" out any value, so that the result of the expression is always the undefined value

**Warning:** The JSON.stringify( -0 ) behavior of "0" is particularly strange when you observe that it's inconsistent with the reverse: JSON.parse( "-0" ) reports -0 as you'd correctly expect.

* numbers include several special values, like NaN (supposedly "Not a Number", but really more appropriately "invalid number"); +Infinity and -Infinity; and -0.
* Simple scalar primitives (strings, numbers, etc.) are assigned/passed by value-copy, but compound values (objects, etc.) are assigned/passed by reference-copy. References are not like references/pointers in other languages -- they're never pointed at other variables/references, only at the underlying values.
# Chpater 3: Natives
**Note:** The Array(..) constructor does not require the new keyword in front of it. If you omit it, it will behave as if you have used it anyway. So Array(1,2,3) is the same outcome as new Array(1,2,3).

**Note:** If you call Date() without new, you'll get back a string representation of the date/time at that moment. The exact form of this representation is not specified in the language spec, though browsers tend to agree on something close to: "Fri Jul 18 2014 00:31:02 GMT-0500 (CDT)".

**Note:** Symbols are not objects, they are simple scalar primitives.

# Chpater 4: Coercion

**Note:** It may not be obvious, but JavaScript coercions always result in one of the scalar primitive (see Chapter 2) values, like string, number, or boolean. There is no coercion that results in a complex value like object or function. Chapter 3 covers "boxing," which wraps scalar primitive values in their object counterparts, but this is not really coercion in an accurate sense.

**Tip:** parseInt(..) has a twin, parseFloat(..), which (as it sounds) pulls out a floating-point number from a string.

**Note:** I call a || b "roughly equivalent" to a ? a : b because the outcome is identical, but there's a nuanced difference. In a ? a : b, if a was a more complex expression (like for instance one that might have side effects like calling a function, etc.), then the a expression would possibly be evaluated twice (if the first evaluation was truthy). By contrast, for a || b, the a expression is evaluated only once, and that value is used both for the coercive test as well as the result value (if appropriate). The same nuance applies to the a && b and a ? b : a expressions.

* `symbol` values cannot coerce to number at all (throws an error either way), but strangely they can both explicitly and implicitly coerce to boolean

**Tip:** Another place where coercion is guaranteed not to bite you is with the typeof operator. typeof is always going to return you one of seven strings (see Chapter 1), and none of them are the empty "" string.

Coercion gets a bad rap, but it's actually quite useful in many cases. An important task for the responsible JS developer is to take the time to learn all the ins and outs of coercion to decide which parts will help improve their code, and which parts they really should avoid.

* Explicit coercion is code which is obvious that the intent is to convert a value from one type to another. The benefit is improvement in readability and maintainability of code by reducing confusion.

* Implicit coercion is coercion that is "hidden" as a side-effect of some other operation, where it's not as obvious that the type conversion will occur. While it may seem that implicit coercion is the opposite of explicit and is thus bad (and indeed, many think so!), actually implicit coercion is also about improving the readability of code.

* Especially for implicit, coercion must be used responsibly and consciously. Know why you're writing the code you're writing, and how it works. Strive to write code that others will easily be able to learn from and understand as well.

# Chpater 5: Grammar

* Note: continue foo does not mean "go to the 'foo' labeled position to continue", but rather, "continue the loop that is labeled 'foo' with its next iteration." So, it's not really an arbitrary goto.

**Note:** If hypothetically && was right-associative, it would be processed the same as if you manually used ( ) to create grouping like a && (b && c). But that still doesn't mean that c would be processed before b. Right-associativity does not mean right-to-left evaluation, it means right-to-left grouping. Either way, regardless of the grouping/associativity, the strict ordering of evaluation will be a, then b, then c (aka left-to-right).

### Review

JavaScript grammar has plenty of nuance that we as developers should spend a little more time paying closer attention to than we typically do. A little bit of effort goes a long way to solidifying your deeper knowledge of the language.

Statements and expressions have analogs in English language -- statements are like sentences and expressions are like phrases. Expressions can be pure/self-contained, or they can have side effects.

The JavaScript grammar layers semantic usage rules (aka context) on top of the pure syntax. For example, { } pairs used in various places in your program can mean statement blocks, object literals, (ES6) destructuring assignments, or (ES6) named function arguments.

JavaScript operators all have well-defined rules for precedence (which ones bind first before others) and associativity (how multiple operator expressions are implicitly grouped). Once you learn these rules, it's up to you to decide if precedence/associativity are too implicit for their own good, or if they will aid in writing shorter, clearer code.

ASI (Automatic Semicolon Insertion) is a parser-error-correction mechanism built into the JS engine, which allows it under certain circumstances to insert an assumed ; in places where it is required, was omitted, and where insertion fixes the parser error. The debate rages over whether this behavior implies that most ; are optional (and can/should be omitted for cleaner code) or whether it means that omitting them is making mistakes that the JS engine merely cleans up for you.

JavaScript has several types of errors, but it's less known that it has two classifications for errors: "early" (compiler thrown, uncatchable) and "runtime" (try..catchable). All syntax errors are obviously early errors that stop the program before it runs, but there are others, too.

Function arguments have an interesting relationship to their formal declared named parameters. Specifically, the arguments array has a number of gotchas of leaky abstraction behavior if you're not careful. Avoid arguments if you can, but if you must use it, by all means avoid using the positional slot in arguments at the same time as using a named parameter for that same argument.

The finally clause attached to a try (or try..catch) offers some very interesting quirks in terms of execution processing order. Some of these quirks can be helpful, but it's possible to create lots of confusion, especially if combined with labeled blocks. As always, use finally to make code better and clearer, not more clever or confusing.

The switch offers some nice shorthand for if..else if.. statements, but beware of many common simplifying assumptions about its behavior. There are several quirks that can trip you up if you're not careful, but there's also some neat hidden tricks that switch has up its sleeve!