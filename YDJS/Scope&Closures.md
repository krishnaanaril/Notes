# Chapter 1: What's Scope?

## Compiler Theory
1. **Tokenizing/Lexing:** breaking up a string of characters into meaningful (to the language) chunks, called tokens. 
2. **Parsing:** taking a stream (array) of tokens and turning it into a tree of nested elements, which collectively represent the grammatical structure of the program. This tree is called an **"AST"**(Abstract Syntax Tree).
3. **Code-Generation:** the process of taking an AST and turning it into executable code. 

**Note:** LHS and RHS meaning "left/right-hand side of an assignment" doesn't necessarily literally mean "left/right side of the = assignment operator". There are several other ways that assignments happen, and so it's better to conceptually think about it as: "who's the target of the assignment (LHS)" and "who's the source of the assignment (RHS)".

**Note:**  It's not really appropriate to think of a function declaration as an LHS look-up assignment in the way we're discussing them here.

## Nested Scope

* If a variable cannot be found in the immediate scope, Engine consults the next outer containing scope, continuing until found or until the outermost (aka, global) scope has been reached.
* If an RHS look-up fails to ever find a variable, anywhere in the nested Scopes, this results in a ReferenceError being thrown by the Engine. It's important to note that the error is of the type *ReferenceError*.

* By contrast, if the Engine is performing an LHS look-up and arrives at the top floor (global Scope) without finding it, and if the program is not running in "Strict Mode" [^note-strictmode], then the global Scope will create a new variable of that name in the global scope, and hand it back to Engine.

* *ReferenceError* is Scope resolution-failure related, whereas *TypeError* implies that Scope resolution was successful, but that there was an illegal/impossible action attempted against the result.
    
# Chapter 2: Lexical Scope

* There are two predominant models for how scope works. 
    * Lexical Scope 
    * Dynamic Scope

* **Lexical Scope:** To define it somewhat circularly, lexical scope is scope that is defined at lexing time. In other words, lexical scope is based on where variables and blocks of scope are authored, by you, at write time, and thus is (mostly) set in stone by the time the lexer processes your code.

## Cheating lexical

* Cheating lexical scope leads to poorer performance.

**Note:** Even though a with block treats an object like a lexical scope, a normal var declaration inside that with block will not be scoped to that with block, but instead the containing function scope.

**Note:** In addition to being a bad idea to use, both eval(..) and with are affected (restricted) by Strict Mode. with is outright disallowed, whereas various forms of indirect or unsafe eval(..) are disallowed while retaining the core functionality.

# Chapter 3: Function vs Block scope

**Note:** The easiest way to distinguish declaration vs. expression is the position of the word "function" in the statement (not just a line, but a distinct statement). If "function" is the very first thing in the statement, then it's a function declaration. Otherwise, it's a function expression.

**Note:** Catch blocks are block scoped.

* Usage of `let` and `const` for block scoped variables.

# Chapter 4: Hoisting

**Note:** Only the declarations themselves are hoisted, while any assignments or other executable logic are left in place. If hoisting were to re-arrange the executable logic of our code, that could wreak havoc.

* Function declarations are hoisted, as we just saw. But function expressions are not.
* Both function declarations and variable declarations are hoisted. But a subtle detail (that can show up in code with multiple "duplicate" declarations) is that functions are hoisted first, and then variables.

# Chapter 5: Scope Closures


> Closure is when a function is able to remember and access its lexical scope even when that function is executing outside its lexical scope

* Whatever facility we use to transport an inner function outside of its lexical scope, it will maintain a scope reference to where it was originally declared, and wherever we execute it, that closure will be exercised.

**Note:** Function-based modules aren't a statically recognized pattern (something the compiler knows about), so their API semantics aren't considered until run-time. That is, you can actually modify a module's API during the run-time (see earlier `publicAPI` discussion).


**Note:** Separate files "foo.js" and "bar.js" would need to be created, with the contents as shown in the first two snippets, respectively. Then, your program would load/import those modules to use them, as shown in the third snippet.

* The contents inside the module file are treated as if enclosed in a scope closure, just like with the function-closure modules seen earlier.

# Appendix A: Dynamic Scope
* JavaScript does not, in fact, have dynamic scope. It has lexical scope. Plain and simple. But the this mechanism is kind of like dynamic scope.
* The key contrast: lexical scope is write-time, whereas dynamic scope (and this!) are runtime. Lexical scope cares where a function was declared, but dynamic scope cares where a function was called from.
# Appendix B: Polyfilling Block Scipe
* Using catch block
# Appendix C: Lexical this