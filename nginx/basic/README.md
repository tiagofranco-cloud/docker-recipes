# Nginx — Basic

A minimal Nginx container serving static content.

## Build
```bash
docker build -t nginx-basic .
```

## Run
```bash
docker run --rm -p 8080:80 nginx-basic
```

Open:
- http://localhost:8080
