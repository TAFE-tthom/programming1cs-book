# Testing Types

We are going to look into two kinds of test types and a framework for testing.
## What is part of a test?

A test-case scenario is made of the following components.

* Description of the  test
* Methodology/Method
* Preconditions
* Postconditions
* Expectations

Each part serves a purpose for ensuring that the test is not contaminated and the scope of the test is well defined. Without a clear goal/description of what is being tested, it may lead to a test site which is unsuitable or useless.

## Whitebox Testing
 
This is typically where we employ some unit testing software, to help analyse the internals of the system and test them independently. This test type is usually reflected as part of **unit testing**.

This is explored further within the **xUnit** section of this chapter.

## Blackbox Testing

User centric testing, without knowledge of the internals, input is given and compared to match the output of the program. This is usually linked to your E2E testing, where you want to testing from one end and see if it reaches and meets the expectation at the other.

A form of blackbox testing that can be conducted easily is by constructing input files that are given to a program. In additional this is typically combined with `diff` and a file which contains the expected output that it will be checked against.


You can use the following code snippet.

```
[user@hostname project] dotnet run < test.in > test.output
[user@hostname project] diff test.output test.out
```

To breakdown the above snippet.

* The first command is running `dotnet run`.
* Instead of the user typing in input using the keyboard, they are using `test.in` instead
* The program will output to `test.output` file
* `diff` is going to compare `test.output` and `test.out`
  * `test.output` is the actual output from the program, this could be wrong or right
  * `test.out` is what we actually expect from the output and `test.output` should match this file

`diff` will either emit output showing the differences or it will provide no output difference, outlining that it is correct.
