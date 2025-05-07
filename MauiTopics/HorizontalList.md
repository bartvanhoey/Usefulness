# Horizontal List

MauiPlayground => UdemyMauiScreenBuildingTechniques => Section5_HorizontalList

## MainPage.xaml.cs

```csharp
namespace HorizontalListMauiApp;

public partial class MainPage : ContentPage
{
    public MainPage()
    {
        InitializeComponent();
            
    }
}

public class MainPageViewModel
{
    public MainPageViewModel() => Devices = ["TV", "Air conditioning", "Video game", "computer"];

    public List<string> Devices { get; set; }
}
```

## MainPage.xaml

```bash
<?xml version="1.0" encoding="utf-8" ?>
<ContentPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:vm="clr-namespace:HorizontalListMauiApp"
             x:Class="HorizontalListMauiApp.MainPage">
    <ContentPage.BindingContext>
        <vm:MainPageViewModel></vm:MainPageViewModel>
    </ContentPage.BindingContext>

    <ScrollView>
        <VerticalStackLayout Spacing="25">
            <Label Text="Devices" />
            <CollectionView ItemsSource="{Binding Devices}" >
                <CollectionView.ItemsLayout>
                    <LinearItemsLayout Orientation="Horizontal" ItemSpacing="20"/>
                </CollectionView.ItemsLayout>
                <CollectionView.ItemTemplate>
                    <DataTemplate>
                        <Border WidthRequest="150" Padding="7" StrokeShape="RoundRectangle 5">
                            <Label Text="{Binding .}" HorizontalOptions="Center" />
                        </Border>
                    </DataTemplate>
                </CollectionView.ItemTemplate>
            </CollectionView>
        </VerticalStackLayout>
    </ScrollView>
</ContentPage>

```
