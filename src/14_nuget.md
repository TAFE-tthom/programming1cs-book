# NuGet

NuGet is a package manager that is used alongside **dotnet** build tool for packaging and distributing libraries. It serves a simular puprose as other software repository systems such as `npm`, `cargo` and `gradle`.

## Using `nuget`

For the most part, `nuget` is not something that needs to be used directly as usage typically will be through the `dotnet` tool. To add a **package** to a dotnet project, you will use `dotnet add package <package name>`. Within each `dotnet` project, you will observe a `.csproj` file that will maintain a list of dependencies, inside an `ItemGroup` as a `PackageReference` entry.

You have the following commands available.

* `dotnet list package` - Will list the packages associated to the project.

* `dotnet add package <package name>` - Will add a package to a project, optionally you can specify the version with `--version <version>` after the package name.

* `dotnet remove package <package name>` - This will remove the package from the project.


Afterwards, you are able to call `dotnet build` which will automatically called `nuget restore` or `dotnet restore` to retrieve the necessary packages and build them.
