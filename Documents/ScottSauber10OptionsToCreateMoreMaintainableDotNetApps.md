# 10 Options for creating more maintainable .NET apps by Scott Sauber

1. Feature folders
2. Treat Warnings as Errors

    add this section in the csproj file of a new Project

    ```bash
        <TreatWarningsAsErrors>true</TreatWarningsAsErrors>
    ```

3. Logging Best Practices
    - use Serilog as logging framework
    - use ILogger everywhere, not Serilog directly
    - use structured logging, not concatenation
    - each log should have key bits of information
    - logs vs metrics vs audits
    - Log Levels: Debug, Info, Warn, Error, Critical

4. Global Authorize Attribute via FallbackPolicy

    ```csharp
        
        builder.Services.AddAuthorization(options => 
        {
            options.FallbackPolicy = new AuthorizePolicyBuilder
                .RequireAuthenticatedUser()
                .Build()
        });
    ```

5. Validation

    Use Fluent Validation instead of Data Annotations

6. Remove the Server Header

    By default ASP.NET Core adds a "Server Header Kestrel"

7. Don't use IOptions

    Solution: Register your Options class directly

    ```csharp

        services.Configure<AppSettings>(Configuration.GetSection("Appsettings"));
        services.AddSingleton(registeredServices => {
            registered.Services.GetRequiredServices<IOptions<AppSettings().Value>>
        })
    
        public AppSettings AppSettings { get;}

        // instead of public IndexModel(IOptions<AppSettings appSettings)
        public IndexModel(AppSettings appSettings)
        {
            // AppSettings = appSettings.Value;
            AppSettings = appSettings;
        }

    ```

8. Version Endpoint

    ```batch
        <Date><BuildNumber><ShortGitSha>    
    ```

9. Structuring a method

    Happy return Path always at the bottom of the method

10. The Indentation Proclamation

    The more intended your code is, the harder it is to read

11. Code smells
    - Methods > 20 lines -> refactor
    - Classes > 200 lines -> refactor
    - Regions -> you probably should add a new class or method
  
12. Build Once, Deploy Many Times
