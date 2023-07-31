# Refactoring Techniques

Our code base is just a big mess, and no one is happy working in it.

Code Excellence is about Discipline!

Any fool can write code that a compiler can understand, it takes real work to write code that a human can understand. (Martin Fowler)

Long methods are a great place for classes to hide. (Bob Martin)

On average, 40% of a code base is clutter

Leave things BETTER than you found them (Boys Scouts)

Small changes over time gives you good code
Never be more than 2 minutes away form checking in and going home

Code on average is read 15-20 times more often than it's written
(=> deleting unnecessary code now, will give you 15-20 extra time in the future)

We can do refactorings in very small pieces each day, and our code is little bit better every day

When are you done with refactorings. You never done!

Refactoring: You don't always need to understand the code while refactoring, as long as the code keeps doing what it did before

Refactoring is the concept of improving the structure and readability of code without changing its behavior

## Arm Yourself! The best warriors have the best weapons

1. Unit Tests (Armor)
2. Tools -> Rider, Resharper, NCrunch, MsTest, xUnit
3. Skills (Patterns)
4. Source control

## What makes code hard to work with

1. No documentation
2. Poor coding standards
3. Other people code
4. Magic numbers
5. Tightly coupled
6. Large Classes
7. Global Variables
8. Bad Names
9. Broken Code
10. Bad Formatting
11. Improper scoping

## Remove the 3 C's

### Clutter

Clutter is anything in your code that does not add value. Harder to read/understand the code

1. Format your code. Choose a default formatting style but be consistent!
2. Delete comments
3. Delete dead code
4. Delete unnecessary code

Deleting the clutter will show you the pattern in the code. The code wants to talk to you.

### Complexity

1. Bad Names
2. Long Methods
3. Deep Conditionals (if/for/while/switch)
4. Magic Numbers
5. Improper Variable Scoping
6. Missing Encapsulation
7. Obscure Code blocks

### Cleverness

If it's simple and elegant, you wouldn't refer to it as 'clever'

1. Cryptic Code
2. Abbreviated Code
3. Hijacking a Method (changing its intent for your own purposes)

## Remove the 3 D's

1. Remove Duplication
2. Remove Duplication
3. Remove Duplication

## Next Steps

Start each task with 25 minutes of cleaning with a co-worker

'Clean Code' by Robert Martin
'Working Effectively with Legacy Code' by Michael Feathers
