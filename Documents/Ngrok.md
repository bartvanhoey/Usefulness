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
