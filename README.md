# Docker Recipes

A curated collection of Dockerfiles and containerization patterns for real-world scenarios.

## Structure
- `nginx/basic` — Nginx container serving static content

## How to use
Each folder is a standalone example. Build and run from inside the example directory.

Example:
```bash
cd nginx/basic
docker build -t nginx-basic .
docker run --rm -p 8080:80 nginx-basic
```
