## EntityFrameworkCore Commands

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
dotnet ef database migrations remove
```


### Howto apply migrations to database

```bash
dotnet ef database update
```

### Howto delete database

```bash
dotnet ef database drop
```
