## Chapter 10 - Classes

* A class should begin with a list of variables. Public static constants should come first.
* Classes should be small. The name of the classes should describe what responsibilties it fulfills.
* We should be able to write a brief description about the class in 25 words witout 'if', 'and', 'or' or 'but'.
* SRP for class is a must.
* A class in which each variable is used by each method is maximally cohesive.
* You should try to separate the variables and methods into two or more classes such that the new classes are more cohesive.
* When classes lose cohesion, split them up.
* Isolationg from change. A client class depending upon concrete details is at risk when those details changes. We should make use of dependancy inversion principles.

## Chapter 11 - Systems

* An optimal system architecture consists of modularised domains of concern, each of which is implemented with Plain Old Java Objects (POJO or Other) objects. The different domains are integrated together with  minimally invasive aspects or aspect like tools. This architecture can be test driven, just like the code. 
* Make just-in time decsions, based on the most recent knowledge. 
* Use standards wisely, when they add demostrable values. 
* Standards make it easier to reuse ideas and components, recruit people with relevant experience, encapsulate good ideas and wire componenets together. But sometimes standsards lose touch with the real needs fo the adopters they are intended to serve.
* Domain specific languages allow all levels of abstraction and all domains in the application to be expressed as POCO's from high level policy to low level details.
* Whether you design systems or individiual modules, never forget to use the simplest thing that can possibly work.

## Chapter 12 - Emergence

* The four rules of simple design
    1. Run all the tests
    2. Contains no duplication
    3. Expresses the intent of the programmer
    4. Minimize the number of classes & methods.
* In an effort to make all classes and methods small, we might create too many tiny classes and methods. So we also keep our function & class counts low.

## Chapter 13 - Concurrency

* Concurrency is a decoupling stragegy. It helps us decouple what gets done form when it gets done. 
* Concurrency Defense Principles
    1. Single Responsibility Principle (SRP)
    2. Take data encapsulation to hear. Serverly limit the access of any data that may be shared
    3. Attempt to partition data into independent substs that can be operated on by independant threads, possibly in different processors. 
    4. Know your framework & library before implementation.
    5. Learn basic algorithms and their solutions.
    6. Avoid using more than one method on a shared object.
    7. Keep your synchronised section as small as possible.
    8. Write tests that have the potential to expose problems and then aim them frequently, with different programastic configurations & system configurations and load. If tests ever fail, trace down the failure. Dont' ignore a failure just becasue the tests pass on a subsequent run.
    9. Get your non-threaded code works first.
    10. Make your threaded code pluggable.
    11. Run with more threads than processors. 
    12. Run your threaded code on all target platforms early & often.

## Chapter 14 - Successive Refinement

* Much of the good software design is simply about partitioning - creating appropriate places to put different kinds of code. 
* Continously keep your code as clean and simple as it can be.

## Chapter 15 - Junit Framework (Skimmed)
## Chapter 16 - Refactoring SerialDate (Skimmed)

* First make it work, then make it right.

## Chapter 17 - Smells & Heuristics

### Comments

* Inappropriate information - Avoid change & metadata. Comments should be reserved for technical notes about the code & design.
* Remove obsolete comment or do not write comments that soom become obsolete.
* Avoid redundant comment. A comment is redundant if it describes the obvious.
* Avoid writing ambiguous & poorly written comments
* Avoid commented-out code. 

### Environment

* Build should be done in a single step.
* Test should be done in a single step.

### Functions

* Avoid too many arguments
* Avoid output arguments, as they are conter intuitive
* Avoid flag/booelan arguments
* Avoid dead functions/unused functions.