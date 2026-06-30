## PowerShell

### Howto convert csv to JSON

```bash
    $items = import-csv .\items.csv | ConvertTo-Json > items.json
```

### Count the numbers of lines in a C# codebase

```bash
    (gci -include *.cs,*.xaml -recurse | select-string .).Count
```

### Export data from a table from (LocalDb)\MSSQLLocalDB to a file

```bash
 bcp GrawSkyDevDb.dbo.InitSondeTable out "C:\CTemp\InitSondeTable.csv" -c -t -S "(localdb)\MSSQLLocalDB" -T
```
