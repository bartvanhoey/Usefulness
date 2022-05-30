## Powershell

### Howto convert csv to JSON

```bash
 $items = import-csv .\items.csv | ConvertTo-Json > items.json
```
