# XUnit and Libraries

We now enter into our first foray of unit-testing. While it is convention to separate logic into applications and libraries, it is possible to use xunit with just an application itself.


## Creating a xunit project

You will utilise the `xunit` template with `dotnet` which will setup and download the necessary components for your project. As per convention, the naming of the testsuite will have the suffix of `.Test`.

```
dotnet new xunit -o Palindrome.Tests
```

We will use the `Palindrome` task as a way to present the usage of `xunit`. In this case we will use a `classlib`. One of the main classes and methods is going to be the following.

```cs
namespace Palindrome;

public class Palindrome
{
	public static bool IsPalindrome(string line)
	{
    // Code here!
		return false;
	}
}
```

Given this static method that is associated with `Palindrome`, we will now update `UnitTest1.cs` to be `PalindromeTest.cs` for clarity sake.

```cs
namespace PalindromeTest;

using Palindrome;

public class PalindromeTestSuite
{
    [Fact]
    public void IsPalindomre_Test_ABBA()
    {
        Assert.True(Palindrome.IsPalindrome("abba"));
    }

    [Fact]
    public void IsPalindomre_Test_RACECAR()
    {
        Assert.True(Palindrome.IsPalindrome("racecar"));
    }

    [Fact]
    public void IsPalindomre_Test_EmptyString()
    {
        Assert.True(Palindrome.IsPalindrome(""));
    }
}
```

Since we have use `xunit`, `Fact` has been imported by default.

*What is `Fact`?*

`Fact` is an attribute that is placed above the method and declares the method a particular test case. Within each method, you can test particular values with an expected outcome using methods associated with `Assert`.

Refer to the following documentation regarding [Assert](https://api.xunit.net/v3/3.2.2/Xunit.Assert.html).
