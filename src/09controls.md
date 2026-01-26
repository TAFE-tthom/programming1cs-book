
# UI Controls

Within Avalonia, you have differnet **controls**, you can think of them as different components that you can use within your `axaml` file. Lets do this by modifying the `MainWindow.axaml` file and changing the text to be within a `TextBlock` control.


```
<TextBlock>Hello To Your FirstUI!</TextBlock>
```

While not much will really change it will show how we can start encapsulating our content withing these controls.

## Controls and Containers

Within Avalonia, we will typically be creating `Window` controls but we can also create custom controls by constructing other `axaml` files that can be used. Importantly, though, we need to be able to indicate how the user-interface will operate.

AvaloniaUI recommends developers leverage layout controls which will involve the following.

* Panel - Lays out all children to fill the bounds of the Panel.

* Canvas - Defins an area within which you can explicitly position child elements using coordinates relative to the Canvas area.

* DockPanel - Defines an area within which you can arrange child elements either horizontally or vertically, relative to each other.

* Grid - Deins a flexible grid area that consistens of columns and rows

* RelativePanel - Arranges child elements relative to other elements or the panel itself.

* StackPanel - Arranges child elements into a single line that can be oriented horizontally or vertically.

* WrapPanel - Positions child elements in equential position from left to right, breaking content to the next line at the edge of the containing box. Subsequent ordering occurs sequentially from top to bottom or right to left, depending on the value of the Orientation property.

Other kinds of controls are going to be used for styling, databinding, text/media, input or anything that can be constructed within the rules of Avalonia and its UI toolkit.

### Layout Controls

As outlined prior, the layout controls are useful for different purposes. Specifically, `Canvas` layouts are useful for applications that are likely to position elements using a coordinate system.

Layouts such as `DockPanel`, `Grid` and `StackPanel` are able to be a little more flexible and adjust based on the dimensions.


## Using `Canvas`

The `Canvas` panel is a very simple but not very flexible panel. Ideally, you will use this panel when creating applications that are likely to perform direct rendering onto the canvas or are going to use coordinates for positioning.

Lets now modify our simple app with `<Canvas>` around the `TextBlock`.

```
<Canvas>
  <TextBlock>Hello World!!</TextBlock>
</Canvas> 
```

The above snippet demonstrates that `TextBlock` is now held inside the `Canvas` layout. We can then position the text using `Canvas.Left`, which will allow us to provide an offset from the left-side of the panel. This is the same with `Canvas.Top` which will provide an offset form the top of the panel.

```
<Canvas>
  <TextBlock Canvas.Left="400">Hello World!!</TextBlock>
</Canvas> 
```


## Using `StackPanel`

While it can feel intuitive to use `Canvas`, it is also limiting, a more versatile layout control is `StackPanel`. The `StackPanel` can seen similar to `flex` in CSS where you are able to specify the orientation of how elements are stacked.

To demonstrate how to use a `StackPanel`, we will go through the following example.

```
<StackPanel Width="200">
    <Rectangle Fill="Red" Height="50"/>
    <Rectangle Fill="Blue" Height="50"/>
    <Rectangle Fill="Green" Height="100"/>
    <Rectangle Fill="Orange" Height="50"/>
</StackPanel>
```

The above example will demonstrate 4 `Rectangle` controls of different colours being placed within the panel. By defualt, the controls are laidout from top-to-bottom (or Vertical) or you can set the orientation to be `Horizontal`, as we do in the following example.

```
<StackPanel Width="200" Orientation="Horizontal">
    <Rectangle Fill="Red" Height="50"/>
    <Rectangle Fill="Blue" Height="50"/>
    <Rectangle Fill="Green" Height="100"/>
    <Rectangle Fill="Orange" Height="50"/>
</StackPanel>
```

Refer to the following, for a more deeper [discussion on layouts](https://docs.avaloniaui.net/docs/basics/user-interface/building-layouts/panels-overview#defining-and-using-a-stackpanel) 

## Buttons and TextBox

Commonly with our UIs we will want to build forms. This will commonly involve labels, buttons and textboxes. Let's use the following snippet and walk through some of the different controls here.

```
<StackPanel Margin="20">
  <TextBlock Margin="0 5" >UserName:</TextBlock>
  <TextBox  Watermark="UsernameHere"/>
  <TextBlock Margin="0 5" >Password:</TextBlock>
  <TextBox PasswordChar="*" Watermark="Enter your password"/>
  <Button Click="LoginHandler">Login</Button>
</StackPanel>
```

The above snippet represents a login panel. It contains a `TextBlock` paired with a `TextBox`. These relate to our label and text input fields.

The `Button` here has an interesting attribute associated. `Click="LoginHandler"` is more than just specifying a name. It is referring to a `method`.

Inside `MainWindow`, we would have a method called `LoginHandler` that will fit the following pattern.

```cs
public void LoginHandler(object sender, RoutedEventArgs args)
{
  //Details related to logging in
}  
```

*Do note, you will need to ensure that `using Avalonia.Interactivity;` is included in this file, otherwise `RoutedEventArgs` will not be accessible. The `LoginHandler` is a method that can access fields, however since both `TextBox`
entries are not using a referenced field, we do not have anything to really do.


### Data Bindings

We will go through a simpler example now and then go back to the login handler. Let's look at this simple counter.

```
<StackPanel>
    <TextBlock x:Name="counter">0</TextBlock>
    <Button Click="IncrementHandler">Increment</Button>
</StackPanel>
```

We can observe the `x:Name="counter"` part of `TextBlock` is referring to the field within `MainWindow`. `Click="IncrementHandler"` is just referring to a method called `IncrementHandler`.

The default value specified is `0` in this case for the `TextBlock`.

```cs

private int ownCounter = 0;

// snipped the rest

public void IncrementHandler(object sender, RoutedEventArgs args)
{
    ownCounter += 1;
    counter.Text = "" + ownCounter;
}
```

The above snippet involves our own integer that we convert to a string and assign to `counter.Text`. `counter` is the name we have assigned to the `TextBlock` and is therefore the `field` name of this component.


So, within the Login example, we would need to handle the following and incorporate some event handling.

```
<TextBlock Margin="0 5" >UserName:</TextBlock>
<TextBox Name="usernameInput" Text="{Binding Username}"  Watermark="UsernameHere"/>
<TextBlock Margin="0 5" >Password:</TextBlock>
<TextBox Name="passwordInput" Text="{Binding Password}" PasswordChar="*" Watermark="Enter your password"/>
```

We are able to associate the `TextChanged` event with a method inside the `MainWindow.axaml.cs` class. Let's update the `TextBox` and associate it with a method.

```
<TextBlock Margin="0 5" >UserName:</TextBlock>
<TextBox Name="usernameInput" Text="{Binding Username}"  Watermark="UsernameHere" TextChanged="UsernameChange"/>
<TextBlock Margin="0 5" >Password:</TextBlock>
<TextBox Name="passwordInput" Text="{Binding Password}" PasswordChar="*" Watermark="Enter your password" TextChanged="PasswordChanged"/>
```

We can then associate it with the following methods.

```cs
public void UsernameChange(object sender, TextChangedEventArgs e) {
    TextBox tbox = (TextBox) sender;
    string tval = tbox.Text;
    username = tval;    
}

public void PasswordChange(object sender, TextChangedEventArgs e) {
    TextBox tbox = (TextBox) sender;
    string tval = tbox.Text;
    password = tval;
}
```

The above methods will convert the current sender and update an associated field.

For more information on the databinding syntax, please refer to [Avalonia's Databinding Syntax Page](https://docs.avaloniaui.net/docs/basics/data/data-binding/data-binding-syntax).
