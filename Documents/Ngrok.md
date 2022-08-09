## Ngrok

## commands

```bash
  ngrok http -region eu https://localhost:44368/
```

## Bat file

Name your file Ngrok.bat and call it from the terminal

```bash
  ngrok.exe http -region eu https://localhost:44368/
```

## Forward multiple ports at once

Find your ngrok.yml configuration file (C:\Users\<your-username>\.ngrok2 )and update its content

```html
  authtoken: <your-authtoken>
  tunnels:
    first:
      addr: 5000
      proto: http    
    second:
      addr: 5001
      proto: http
```

Open a command prompt and run the command below:

```bash
  ngrok start --all
```

## batch script to copy Ngrok tunnel url to an appsettings file

```bash
set sourceFile="C:\path\appsettings.debug.json"
set portNumber=44368

@echo off
setlocal disabledelayedexpansion

start ngrok.exe http -region eu https://localhost:%portNumber%/

timeout 5 > NUL

if not exist "C:\TEMP_NGROK\" mkdir "C:\TEMP_NGROK\"

for /F %%I in ('curl -s http://127.0.0.1:4040/api/tunnels ^| jq -r .tunnels[0].public_url') do set ngrokTunnel=%%I
echo %ngrokTunnel%

for /f "tokens=1* delims=]" %%a in ('find /n /v "" %sourceFile%') do (
  echo %%b|findstr /rc:"\ *\"AuthorityUrl\"\ :\ \".*\"" >nul && (
    for /f "delims=:" %%c in ("%%b") do echo %%c: "%ngrokTunnel%",
    ) || echo/%%b
)>>C:\TEMP_NGROK\temp.json 2>nul

for %%I in (C:\TEMP_NGROK\temp.json) do for /f "delims=, tokens=* skip=1" %%x in (%%I) do echo %%x >> "%%I.new"

move /Y "C:\TEMP_NGROK\temp.json.new" %sourceFile% > nul

del C:\TEMP_NGROK\temp.json
rmdir /s /q "C:\TEMP_NGROK\"



```
