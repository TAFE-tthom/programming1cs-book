# Templates and Setup

Setting up projects that use a particular framework are likely to have their own template in which to build from. This is particularly common within dotnet user-interfaces.

The UI framework we will employ here is AvaloniaUI. This toolkit is a cross-platform toolkit that will work on your system regardless if you are on Windows, MacOS or Linux.

## Installing Templates

We will now dive into the world of the `dotnet` command again and attach a new set of sources to use. Within your command line, you should be able to run.

```
dotnet new install Avalonia.Templates
```

The above command installs a set of templates that the dotnet command can now use as well as any IDE that may retrieve the list of templates.


You should now observe a success that the following templates have been installed.

```
Avalonia .NET App                             avalonia.app                [C#],F#     Desktop/Xaml/Avalonia/Windows/Linux/macOS
Avalonia .NET MVVM App                        avalonia.app                [C#],F#     Desktop/Xaml/Avalonia/Windows/Linux/macOS
Avalonia Cross Platform Application           avalonia.xplat              [C#],F#     Desktop/Xaml/Avalonia/Web/Mobile
Avalonia Resource Dictionary                  avalonia.resource                       Desktop/Xaml/Avalonia/Windows/Linux/macOS
Avalonia Styles                               avalonia.styles                         Desktop/Xaml/Avalonia/Windows/Linux/macOS
Avalonia TemplatedControl                     avalonia.templatedcontrol   [C#],F#     Desktop/Xaml/Avalonia/Windows/Linux/macOS
Avalonia UserControl                          avalonia.usercontrol        [C#],F#     Desktop/Xaml/Avalonia/Windows/Linux/macOS
Avalonia Window                               avalonia.window             [C#],F#     Desktop/Xaml/Avalonia/Windows/Linux/macOS
```

Afterwards, we should be able to setup our own templates within the command line.


## Setting up a project

Similar to constructing a console application, you are able to construct an AvaloniaUI application using the following command.

```
dotnet new avalonia.app -o FirstUIApp
```

The above will use the `avalonia.app` template and the `FirstUIApp` will be the name of the project. Listing the directory you will notice a few different files than your standard `console` template. Namely, the `.axaml` and a `.axaml.cs`.

The two files play a particular role here.

* `App.axaml` and its `.cs` - These files are for the applicaiton and typically do not provide much say regarding what the windows look like. However they will have theme request information (Light and Dark mode) and styles that may be defaulted to.

* `MainWindow.axaml` - This relates to the window that will be associated with the application. You will notice the text when you run the application is also present in this file.

## UI structuring and why `axaml`?

This can seem a little confusing for many developers who are just entering into their first endeavour of creating and designing a user interface. So it can seem strange to suddenly find ourself using a different tool besides C# to make these user interfaces.

*Why are we using `axaml` files?*

The reason comes down to separating the layout from the code itself, this layout can be expressed using a markup language, in this case, a variant of `XML`. `XAML` has been a markup language part of the dotnet ecosystem for a very long time and it is where the XAML entries can map to .net objects.

*Wouldn't this be inefficient to writing it in C#?*

**No** although with the caveat that there is possibly or was overhead in parsing and translating it into C# objects but that such construction is equivalent to parsing a HTML file. It is trivial and the format affords struture.
