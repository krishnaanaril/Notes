## Chapter 01 - Clean Code

* Programmers should convey the challenges to the managers. It is too unprofessional to bend to the will of managers who don't understand the risks of making messes. An analogy of developer as doctor and manager as patient is presented and made a lot of sense. 
* The only way to go fast is to keep the code as clean as possible.
* Quoting Bjourne Stroustrap - Bad code tries to do so much, clean code is focused and elegant.
* Developer spend a lot of time reading the code. So If he/she want to go fast, make it easy to read.
* The Boy Scout Rule: Leave the campground cleaner that you found it.

## Chapter 02 - Meaningful Names

* Use Intention - Revealing Names
* If a name requires a comment, then name doesn't reveal its intent.
* Avoid disinformation - Programmers must avoid leaving false clues that obscure the meaning of code. 
* Make meaningful distinctions - Developers create problems for themselves, when they write code to satisfy a compiler or interpreter. Distinguish names in such a way that the reader know what the differences offer.
* User pronounceable names - 
* Use searchable names - Single letter names and numeric constants have a particular problem in that they are not easy to  locate across a body of text. **The length of a name should correspond to the size of its scope**
* Avoid encodings
* You should be using an editing environment that highlights or colorizes members to make them distinct.
* Avoid mental mapping - Prefer clarity over smartness.
* Classes and Objects should have noun or noun phrases. A class name should not be a verb.
* Methods should have verb or verb phrase names.
* Don't be cute - Avoid fancy naming conventions. Say what you mean and mean what you say.
* Pick one work per concept. Eg. avoid the use of fetch, retrieve and get for the same concept in different contexts.
* Use solution domain names & problem domain names based on the context.

## Chapter 03 - Functions

* Small - The first rule of function is that it should be small.
* Blocks and Indenting - Conditional blocks should be one line long (may be another function call). Function should not be large enought to hold nested structures.
* Do one thing - Functions should do one thing. They should do it well. They should do it only.
* One level of abstraction per function.
* Use polymorphism to avoid the using of repeated switch statements.
* Use descriptive names - A long descriptive name is better than a long descriptive comment (Really? I'm not sure).
* Function arguments - More than three requires a special justificaiton - and then shouldn't be used anyway.
* Flag arguments are ugly. Passing a boolean into a function is truly a terrible practice. It's better to create two different functions.
* If we have more than one argument to a function, it is better to wrap them into a class.
* If possible function name should be name in such a way that it give info about the intent of the function & arguments.
* Have no side effects. It should be a pure function.
* If a function have temporal coupling, it should be advertised in the name.
* Anything that forces you to check the function signature is equivalent to a double-take. It's a cognitive break and should be avoided.
* Command - Query separation. Functions should either do or answer something.
* Prefer exceptions to return error codes. If we use exceptions, then error processing code can be separated from the happy path code and can be simplified.
