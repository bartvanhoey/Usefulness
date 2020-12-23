## .NET Commands

### Howto create a new solution

```bash
dotnet new sln -n [YourSolutionName]
```

### How to create a new class library project

```bash
>dotnet new classlib -n [YourProjectName]]
```

### Howto add project to solution

```bash
dotnet sln add [yourProjectName]\[yourProjectName].csproj
```

### Howto add reference to other project

 ```bash
 dotnet add reference ../../src/Volo.Abp.AspNetCore.Components.WebAssembly.BasicTheme/Volo.Abp.AspNetCore.Components.WebAssembly.BasicTheme.csproj
 ```
