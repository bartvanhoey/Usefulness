## .NET Commands

## Solution

### Howto create a new solution

```bash
dotnet new sln -n [YourSolutionName]
```

### How to create a new class library project

```bash
dotnet new classlib -n [YourProjectName]
```

### Howto add project to solution

```bash
dotnet sln add [yourProjectName]\[yourProjectName].csproj
```

### Howto add reference to other project

 ```bash
 dotnet add reference ../../src/Volo.Abp.AspNetCore.Components.WebAssembly.BasicTheme/Volo.Abp.AspNetCore.Components.WebAssembly.BasicTheme.csproj
 ```

## Packages

### Add package to project

```bash
dotnet add package [PackageName]
```

## User Secrets

You can find the user secrets in following folder: `C:\Users\bartv\AppData\Roaming\Microsoft\UserSecrets`

### Init

```bash
dotnet user-secrets init
```

### List

```bash
dotnet user-secrets list
```

### Set a secret

```bash
dotnet user-secrets set "AuthorApiKey" "xyz1@3"
```

### Remove a secret

```bash
dotnet user-secrets remove "AuthorApiKey"
```

### Remove all secret

```bash
dotnet user-secrets clear
```
