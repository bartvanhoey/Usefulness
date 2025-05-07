# BindablePropertyGenerator source code generator

when creating custom controls in .NET MAUI you need to write a lot of boilerplate code, like the code below, to be able to use bindable properties
With the use of 2 nuget packages **BindablePropertyGenerator.SourceGenerators** and **BindablePropertyGenerator.Attributes** you can greatly reduce the amount of boilerplate.

## Amount of boilerplate code for 4 properties without using these nuget packages

```csharp
// ReSharper disable MemberCanBePrivate.Global
namespace ReusableControlsTest.Controls;

public partial class DeviceCard
{
    public DeviceCard()
    {
        InitializeComponent();
    }

    public static readonly BindableProperty TitleProperty = CreateBindableProperty(nameof(Title), "");
    public static readonly BindableProperty IconUriProperty = CreateBindableProperty(nameof(IconUri), "");
    public static readonly BindableProperty NameProperty = CreateBindableProperty(nameof(Name), "");
    public static readonly BindableProperty StatusProperty = CreateBindableProperty(nameof(Status), "");

    public string Status
    {
        get => (string)GetValue(StatusProperty);
        set => SetValue(StatusProperty, value);
    }
    
    public string IconUri
    {
        get => (string)GetValue(IconUriProperty);
        set => SetValue(IconUriProperty, value);
    }
    
    public string Name
    {
        get => (string)GetValue(NameProperty);
        set => SetValue(NameProperty, value);
    }
    
    public string Title
    {
        get => (string)GetValue(TitleProperty);
        set => SetValue(TitleProperty, value);
    }
    
    
    private static BindableProperty CreateBindableProperty<T>(string propertyName, T defaultValue, BindableProperty.BindingPropertyChangedDelegate? propertyChanged = null, BindingMode bindingMode = BindingMode.TwoWay) 
        => BindableProperty.Create(propertyName: propertyName, returnType: typeof(T), declaringType: typeof(DeviceCard), defaultValue: defaultValue, propertyChanged: propertyChanged, defaultBindingMode: bindingMode);
}

```

## Code for 4 properties after using using these nuget packages

```bash
dotnet add package BindablePropertyGenerator.SourceGenerators
dotnet add package BindablePropertyGenerator.Attributes
```

```csharp
// 22 Lines of code less than the example above
namespace ReusableControlsTest.Controls;

public partial class DeviceCard
{
    public DeviceCard()
    {
        InitializeComponent();
    }
    
    [GenerateBindableProperty(typeof(string))] public static readonly BindableProperty TitleProperty = CreateBindableProperty(nameof(Title), "");
    [GenerateBindableProperty(typeof(string))] public static readonly BindableProperty IconUriProperty = CreateBindableProperty(nameof(IconUri), "");
    [GenerateBindableProperty(typeof(string))] public static readonly BindableProperty NameProperty = CreateBindableProperty(nameof(Name), "");
    [GenerateBindableProperty(typeof(string))] public static readonly BindableProperty StatusProperty = CreateBindableProperty(nameof(Status), "");
}

```
