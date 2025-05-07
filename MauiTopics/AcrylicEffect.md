# How to apply an Acrylic Effect in a MAUI app

MauiPlayground => UdemyMauiScreenBuildingTechniques => AcrylicEffectApp

## install nuget package AcrylicView.Maui

```bash
dotnet add package AcrylicView.Maui
```

## Setup AcrylicView in MauiProgram.cs

```csharp
public static class MauiProgram
{
    public static MauiApp CreateMauiApp()
    {
        var builder = MauiApp.CreateBuilder();
        builder
            .UseMauiApp<App>()
            .UseAcrylicView()
            .ConfigureFonts(fonts =>
            {
                fonts.AddFont("OpenSans-Regular.ttf", "OpenSansRegular");
                fonts.AddFont("OpenSans-Semibold.ttf", "OpenSansSemibold");
            });

#if DEBUG
        builder.Logging.AddDebug();
#endif

        return builder.Build();
    }
}
```

## Make use of the AcrylicView in your page

```bash
<?xml version="1.0" encoding="utf-8" ?>
<ContentPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="AcrylicEffectApp.MainPage"
             xmlns:acrylic="clr-namespace:Xe.AcrylicView;assembly=Xe.AcrylicView" >
    <Grid>
        <Image Source="chair.png" Aspect="Fill" />
        <VerticalStackLayout>
            <Border HeightRequest="100"  VerticalOptions="Start" StrokeThickness="0" Margin="10" BackgroundColor="#66FFFFFF" >
                <Label Text="Hello World" FontSize="26" HorizontalOptions="Center" VerticalOptions="Center" ></Label>
            </Border>

            <acrylic:AcrylicView VerticalOptions="Center"  HeightRequest="100"  EffectStyle="Light"    Margin="10"  >
                <Label Text="Hello World" FontSize="26" HorizontalOptions="Center" VerticalOptions="Center" ></Label>
            </acrylic:AcrylicView>
            <acrylic:AcrylicView VerticalOptions="End"  HeightRequest="100"  EffectStyle="Dark" Margin="10"  >
                <Label Text="Hello World" FontSize="26" HorizontalOptions="Center" VerticalOptions="Center" ></Label>
            </acrylic:AcrylicView>

            <acrylic:AcrylicView VerticalOptions="End" Padding="20" HeightRequest="100"  EffectStyle="Custom" TintColor="Orange" TintOpacity=".15"   Margin="10"  >
                <Label Text="Hello World" FontSize="26" HorizontalOptions="Center" VerticalOptions="Center"  ></Label>
            </acrylic:AcrylicView>

            <acrylic:AcrylicView CornerRadius="20,20,20,20" VerticalOptions="End" Padding="20" HeightRequest="100"  EffectStyle="Custom" TintColor="Orange" TintOpacity=".15"   Margin="10"  >
                <Label Text="Hello World" FontSize="26" HorizontalOptions="Center" VerticalOptions="Center"  ></Label>
            </acrylic:AcrylicView>
        </VerticalStackLayout>
    </Grid>
</ContentPage>

```
