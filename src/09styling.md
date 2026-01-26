# Styling and Resources

Styling within Avalonia has been referenced and known similar to CSS. There is a mechanism for selecting particular entries (like querying a HTML document) and specifying the property it will inherit.

Let's use the following example to work with.

```
<Window.Styles>
  <Style Selector="TextBlock.h1">
      <Setter Property="FontSize" Value="24"/>
      <Setter Property="FontWeight" Value="Bold"/>
  </Style>
</Window.Styles>
<StackPanel Margin="20">
   <TextBlock Classes="h1">Heading 1</TextBlock>
</StackPanel>
```

The above example will use the `Style` entry and specify `Setter` with a `Property` attribute that will be associated with a value.

## Selectors

**TODO**
