## Chapter 04 - Comments

* The proper use of comments is to compensate for our failure to express ourself in code.
* Inaccurate comments are far more worse than no comments at all. They become outdated and misled mostly because of developers inability to maintian them.
* Comments do not make up for bad code. 
* Legal comments, informative & TODO comments are acceptable.
* Don't use a comment when you can use a function or variable.
* Avoid commenting out code practice, and make full use of source control for that. 
* Connection between the comment and the code it describes should be obvious.

## Chapter 05 - Formatting

* Vertical formatting - Each blank line is a visual cue that identifies a new & separate concept.
* Vertical density - Lines of code that are tightly related should appear vertically dense.
* Vertical distance - Concepts that are closely related should be kept vertically close to each other.
* Variable declarations - Variables should be declared as close to their usage as possible.
* Control variables for loops should be declared within the loop statement.
* Instance variables, on the other hand should be declared at the top of the class.
* Dependent functions - If one function calls another, they should be vertically close.
* Vertical ordering - A function that is called should be below a function that does the calling.
* Horizontal ordering - We should strive to keep our lines short.
* Indentation - To make the hierarchy of super visible, we indent the lines of source code in proportion to their position in hierarchy.
* Team Rules - A team of developers should agree upon a single formatting style and then every member of that team should follow it.

## Chapter 06 - Objects & Data Structures

* Data abstraction - Express data in abstract terms. Hide implementation detail from the users. 
* In any complex system there are going to be times when we want to add enw data types rather than new functions. For these cases objects and OO are most appropriate. On the other hand, there will also be times when we'll want to add new functions as opposed to data types. In that case procedural code & data structures will be more appropriate.
* The Law of Demeter - A module should not know about the innards of the object it manipulates
* Objects should expose behaviour and hide data.