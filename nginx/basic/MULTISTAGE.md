# Docker Image Optimization with Multi-stage

This example demonstrates the impact of multi-stage builds when creating container images.

## Initial version (Ubuntu + Nginx)
- Base: Ubuntu 22.04
- Size: ~53MB+
- Included packages and build tools
- Not optimized for production

## Optimized version (Multi-stage + Alpine)
- Base: Alpine Linux
- Size: ~7MB
- Only runtime dependencies included
- Reduced attack surface
- Faster pull and deployment

## Size comparison

| Version | Image size |
|--------|-----------|
| Initial Ubuntu image | ~53MB |
| Improved version | ~7MB |

## Why multi-stage matters

Multi-stage builds allow separation between:
- build environment
- runtime environment

This ensures that only the necessary artifacts go to the final image, improving:
- security
- performance
- deployment speed

## Build and run

```bash
docker build -t nginx-multistage .
docker run -p 8080:80 nginx-multistage
