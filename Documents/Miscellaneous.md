## Miscellaneous

## Check if specific port is in use and kill process

```bash
netstat -aon | find "7215"
taskkill /F /pid 36684
```

## Generate random Secret Key using an OpenSSL command in Git Bash

```bash
openssl rand -base64 32
```
