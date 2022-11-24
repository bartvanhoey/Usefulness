[Git](Documents/Git.md) | [EF Core](Documents/EntityFrameworkCore.md) | [ABP cli](Documents/ABPcli.md) | [.NET](Documents/DotNet.md) | [Vim Editor](VimEditor.md) | [Visual Studio Code](Documents/VsCode.md) | [Notepad++](Documents/NotepadPlusPlus.md) |  [Ngrok](Documents/Ngrok.md)

[Docker](Documents/Docker.md) | [Kubernetes](Documents/Kubernetes.md) | [Rider](Documents/Rider.md) | [Azure Kubernetes Service](Documents/AKS.md) | [Powershell](Documents/PowerShell.md)

## My Top Ten CommandLine Commands

1. Create a new ABP Framework project

    ```bash
    abp new MyAbpApp -u blazor -o MyAbpApp
    ```

2. Install or update the latest ABP CLI

    ```bash
    dotnet tool install -g Volo.Abp.Cli || dotnet tool update -g Volo.Abp.Cli
    ```

3. Update EF tool

    ```bash
    dotnet ef --version
    dotnet tool update --global dotnet-ef
    ```

4. Add EF migrations to a project

    ```bash
    dotnet ef migrations add <MigrationName>
    ```

5. Remove EF migrations to a project

    ```bash
    dotnet ef migrations remove
    ```

6. Apply EF migrations to the database

    ```bash
    dotnet ef database update
    ```

7. Remove EF migrations already applied to the database

    ```bash
    dotnet ef database update <MigrationName-to-which-you-want-to-revert>
    dotnet ef migrations remove
    ```

8. Add a project to your solution

    ```bash
    dotnet sln add [yourProjectName]\[yourProjectName].csproj
    ```

9. Add a reference to a project from another project

    ```bash
    dotnet add reference ../../src/Volo.Abp.AspNetCore.Components.WebAssembly.BasicTheme/Volo.Abp.AspNetCore.Components.WebAssembly.BasicTheme.csproj
    ```

10. Add a Nuget package to your project

    ```bash
    dotnet add package [PackageName]
    ```

