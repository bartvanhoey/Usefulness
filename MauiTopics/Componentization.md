# How to create a usable component in MAUI

MauiPlayground => UdemyMauiScreenBuildingTechniques => Componentization

## Create a Card Component

```bash

// Card.xaml

<?xml version="1.0" encoding="utf-8"?>

<ContentView 
    x:Name="MyCardControl"
    xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
    xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
    x:Class="Componentization.Components.Card"
    BindingContext="{x:Reference MyCardControl}">
    <Border WidthRequest="120" HeightRequest="145" Stroke="Black" StrokeShape="RoundRectangle 10">
        <VerticalStackLayout>
            <Image Source="{Binding ImageSource}"></Image>
            <Label Text="{Binding Title}" VerticalOptions="End" HorizontalOptions="Center" ></Label>
        </VerticalStackLayout>
    </Border>
</ContentView>

```

```csharp

// Card.xaml.cs

namespace Componentization.Components;

public partial class Card
{

    public static readonly BindableProperty TitleProperty = BindableProperty.Create(nameof(Title), typeof(string), typeof(Card));
    public static readonly BindableProperty ImageSourceProperty = BindableProperty.Create(nameof(ImageSource), typeof(string), typeof(Card));

    public string Title
    {
        get => (string)GetValue(TitleProperty);
        set => SetValue(TitleProperty, value);
    }

    public string ImageSource
    {
        get => (string)GetValue(ImageSourceProperty);
        set => SetValue(ImageSourceProperty, value);
    }

    public Card()
    {
        InitializeComponent();
    }
}

```

## How to use the Card Component

```bash
# MainPage.xaml
<?xml version="1.0" encoding="utf-8" ?>
<ContentPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:components="using:Componentization.Components"
             x:Class="Componentization.MainPage">
    <ScrollView>
        <VerticalStackLayout>
            <components:Card Title="Menu" 
                             ImageSource="menu_dots_icon.png" />

            <components:Card Title="Configuration" 
                             ImageSource="configuration_settings_icon.png"/>

        </VerticalStackLayout>
    </ScrollView>
</ContentPage>
```
