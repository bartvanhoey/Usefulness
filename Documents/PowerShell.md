## Powershell

### Howto convert csv to JSON

```bash
    $items = import-csv .\items.csv | ConvertTo-Json > items.json
```

### Count the numbers of lines in a C# codebase

```bash
    (gci -include *.cs,*.xaml -recurse | select-string .).Count
```


