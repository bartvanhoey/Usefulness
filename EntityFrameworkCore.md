## EntityFrameworkCore Commands


### Howto install EntityFramework tools

```bash
dotnet tool install --global dotnet-ef
```

### Howto update EntityFramework tools

```bash
dotnet tool update --global dotnet-ef
```

### Howto check version of EntityFrameworkCore

```bash
dotnet ef --version
```

### Howto add a migration

```bash
dotnet ef migrations add <MigrationName>
```

### Howto remove a migration not applied to database yet

```bash
dotnet ef migrations remove
```

### Howto revert a migration ALREADY applied to database

```bash
dotnet ef database update <MigrationName-to-which-you-want-to-revert>
dotnet ef migrations remove
```

You need to run the remove command as many times as needed to go back to the MigrationName-to-which-you-want-to-revert

### Howto apply migrations to database

```bash
dotnet ef database update
```

### Howto get list of migrations

```bash
dotnet ef migrations list
```

### Howto delete database

```bash
dotnet ef database drop
```
