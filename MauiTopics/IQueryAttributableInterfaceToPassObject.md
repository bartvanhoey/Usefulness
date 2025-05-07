# Use of IQueryAttributable interface to Pass an Object when Navigating to other Page

MauiPlayground => MyMauiNewsApp

```bash
// HomePage.xaml

<?xml version="1.0" encoding="utf-8"?>

<ContentPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:viewmodels="using:MyMauiNewsApp.ViewModels"
             xmlns:models="using:MyMauiNewsApp.Models"
             x:Class="MyMauiNewsApp.Views.HomePage">
    <ContentPage.Resources>
        <Style TargetType="StackLayout" x:Key="HeaderStack">
            <Setter Property="Margin" Value="20,16,20,14"/>
            <Setter Property="Orientation" Value="Horizontal"/>
            <Setter Property="Padding" Value="20,0"/>
        </Style>
        <Style TargetType="Label" x:Key="SectionHeading">
            <Setter Property="FontFamily" Value="NotoSerifBold"/>
            <Setter Property="FontSize" Value="20"/>
            <Setter Property="HorizontalOptions" Value="StartAndExpand"/>
        </Style>
        <Style TargetType="Label" x:Key="ShowAll">
            <Setter Property="HorizontalOptions" Value="End"/>
            <Setter Property="FontSize" Value="16"/>
            <Setter Property="TextColor" Value="{StaticResource Primary}"/>
            <Setter Property="VerticalOptions" Value="End"/>
        </Style>
        <DataTemplate x:DataType="models:Article" x:Key="ArticleTemplate">
            <StackLayout Orientation="Vertical" Margin="20,0,0,0" WidthRequest="300" HeightRequest="260">
                <StackLayout.GestureRecognizers>
                    <TapGestureRecognizer CommandParameter="{Binding .}" 
                                          Command="{Binding Source={RelativeSource AncestorType={x:Type viewmodels:HomeViewModel}}, Path=TappedCommand}"/>
                </StackLayout.GestureRecognizers>
                <Border Padding="0" Stroke="Transparent">
                    <Image Source="{Binding ImageURL}" HeightRequest="180" WidthRequest="300" Aspect="AspectFill" />
                </Border>
                <Label Text="{Binding Title}" Margin="0,4,0,0" FontSize="18" FontFamily="PoppinsSemibold" MaxLines="2"/>
                <StackLayout Orientation="Horizontal" Spacing="4">
                    <Label Text="{Binding Category}" TextColor="{StaticResource Primary}"/>
                    <Label Text="·" FontAttributes="Bold" TextColor="{StaticResource Gray200}"/>
                    <Label Text="{Binding Time}" TextColor="{StaticResource Gray200}"/>
                </StackLayout>
            </StackLayout>
        </DataTemplate>
    </ContentPage.Resources>
    <ContentPage.Content>
        <ScrollView>
            <VerticalStackLayout>
                <StackLayout Style="{StaticResource HeaderStack}">
                    <Label Text="Latest News" Style="{StaticResource SectionHeading}"/>
                    <Label Text="Show All" Style="{StaticResource ShowAll}" />
                </StackLayout>
                <FlexLayout BindableLayout.ItemsSource="{Binding Tags}" Wrap="Wrap" Margin="20,0">
                    <BindableLayout.ItemTemplate>
                        <DataTemplate>
                            <Border BackgroundColor="#f2f2f2" Stroke ="Transparent"  StrokeShape="RoundRectangle 5" Padding="8,2" Margin="0,0,4,10">
                                <Label Text="{Binding .}" FontFamily="Poppins" VerticalOptions="Center"></Label>
                            </Border>
                        </DataTemplate>
                    </BindableLayout.ItemTemplate>
                </FlexLayout>

                <BoxView/>

                <StackLayout Style="{StaticResource HeaderStack}">
                    <Label Text="Latest News" Style="{StaticResource SectionHeading}"/>
                    <Label Text="Show All" Style="{StaticResource ShowAll}" />
                </StackLayout>

                <ScrollView Orientation="Horizontal" HorizontalScrollBarVisibility="Never">
                    <StackLayout Orientation="Horizontal" Spacing="10" BindableLayout.ItemsSource="{Binding LatestArticles}" BindableLayout.ItemTemplate="{StaticResource ArticleTemplate}" ></StackLayout>
                </ScrollView>

                <BoxView/>

                <StackLayout Style="{StaticResource HeaderStack}">
                    <Label Text="Popular articles" Style="{StaticResource SectionHeading}"/>
                    <Label Text="Show All" Style="{StaticResource ShowAll}"/>
                </StackLayout>

                <ScrollView Orientation="Horizontal" HorizontalScrollBarVisibility="Never">
                    <StackLayout Orientation="Horizontal" Spacing="10" BindableLayout.ItemsSource="{Binding PopularArticles}" BindableLayout.ItemTemplate="{StaticResource ArticleTemplate}" ></StackLayout>
                </ScrollView>


            </VerticalStackLayout>
        </ScrollView>

    </ContentPage.Content>
</ContentPage>

// HomePage.xaml.cs

public partial class HomePage : ContentPage
{
    public HomePage(INewsService newsService)
    {
        InitializeComponent();
        this.BindingContext = new HomeViewModel(newsService);
    }
}

// HomeViewModel.cs

public class HomeViewModel
{
    public HomeViewModel(INewsService news)
    {

        TappedCommand = new Command<Article>((article) =>
        {
            var query = new Dictionary<string, object>
            {
                { "article", article }
            };
            Shell.Current.GoToAsync("//home/article", query);
        });
    }
    
    public Command<Article> TappedCommand { get; set; }
    
}

// ArticlePage.xaml.cs

public partial class ArticlePage : ContentPage, IQueryAttributable
{
    private readonly INewsService _newsService;

    public ArticlePage(INewsService newsService)
    {
        _newsService = newsService;
        InitializeComponent();
    }

    public void ApplyQueryAttributes(IDictionary<string, object> query)
    {
        if (query.FirstOrDefault(kvp => kvp.Key.Equals("article")).Value is Article article) 
            BindingContext = new ArticleViewModel(_newsService, article);
    }
}

// ArticleViewModel.cs

public class ArticleViewModel
{
    public ArticleViewModel(INewsService news, Article article)
    {
        Title = article.Title;
        ImageURL = article.ImageURL;
        Body = news.GetArticleBody(article.Id);
        Time = article.Time;
    }

    public string Title { get; set; }
    public string ImageURL { get; set; }
    public string Body { get; set; }
    public string Time { get; set; }
}

```
