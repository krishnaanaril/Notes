## Chapter 07 - Error handling

* Error hadling is important, but if it obscures logic it is wrong.
* Use exceptions rather than return codes
* Write your try-catch finally statement first.
* Use unchecked exceptions. Checked exceptions can sometimes be useful if you are writing a critical library, you must catch them. But in general app development the dependency costs out weigh the benefits.
* Create informative error messages and pass them along with your exception.
* Often a single exception class is fine for a particular area of code. The information sent with exception can distinguish errors. Use differenct classes only you want to catch one exception and allow the other ones to pass through.
* Dont' return nulls. Dont' pass nulls.

## Chapter 08 - Boundaries

* We must cleanly integrate foreign code with our own. 
* Learning tests are tests on third party libraries to check whether they work as we think. Learning tests are better than free. 
* If the third party change the package in some way incompatiable with our tests, will find out right away.
* Code at the boundaries needs clear separation and tests that define expectations.

## Chapter 09 - Unit tests

* The three laws of TDD
    1. You may not wirte production code until you've written a failing unit test.
    2. You may not write more of a unit test than is sufficient to fail, and not compiling is failing.
    3. You may not write more production code than is sufficient to pass the currently failing test.
* Keep tests clean. TEst code is just as important as production code.
* It is unit tests that keep our code flexible, maintainable and reuseable.
* Readability is perhaps more important in unit test than it is in production code.
* There are things that you might never do in a production environment that are perfectly fine in a test environment, which involves memory & CPU efficiency but never cleanliness.
* One assert per test is a good guideline, But sometimes it causes code duplication, so we should try to minimise the number of assets.
* Single concept per test.
* F.I.R.S.T - Rules for clean tests
    1. Fast
    2. Independant
    3. Repeatable
    4. Self-Validating - Should've boolean output
    5. Timely - It is better to write unit tests before production to avoid writing non-testable code.



