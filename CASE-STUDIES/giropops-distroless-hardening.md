# From 415MB to 31MB: Hardening a Python Container with Distroless

## Context

One of the most common problems in real-world container environments is not functionality —  
it's security and efficiency.

Many containers run in production today:
- with unnecessary packages
- with large attack surface
- with known vulnerabilities
- without clear runtime separation

This case study documents the process of transforming a functional container into a production-grade hardened image.

---

## Initial State

The original container image:

- ~415MB
- Multiple HIGH and CRITICAL vulnerabilities
- Contained build tools
- Large base image
- Not optimized for distribution
- High attack surface

It worked.  
But it was not production-ready.

---

## Engineering Goals

The objective was not only to make the image smaller.

The real goals:

- Reduce vulnerabilities to zero
- Minimize runtime footprint
- Apply DevSecOps mindset
- Use hardened base images
- Improve supply chain trust
- Simulate production-grade container delivery

---

## Strategy

### Multi-stage build
Separated build and runtime environments.

This ensures:
- build dependencies stay out of final image
- runtime stays minimal
- smaller SBOM
- less attack surface

### Virtualenv isolation
Python dependencies isolated from system environment.

Benefits:
- predictable runtime
- no global pollution
- easier dependency control

### Distroless Chainguard base image
The final runtime uses Chainguard's Wolfi-based image.

Key advantages:
- minimal OS footprint
- continuously patched
- no package manager
- no shell
- reduced CVE exposure

---

## Final Results

| Metric | Before | After |
|-------|-------|------|
| Image size | ~415MB | ~31MB |
| Vulnerabilities | HIGH/CRITICAL present | 0 findings |
| Runtime footprint | Large | Minimal |
| Production readiness | Low | High |

Validated using:
- Trivy
- Docker Scout

---

## Security Impact

Smaller images are not just about performance.

They directly impact:
- CVE exposure
- SBOM size
- patching surface
- pull time in clusters
- registry storage
- deployment speed

A hardened container improves the entire delivery pipeline.

---

## Lessons Learned

Container engineering is not just about making things run.

It's about:
- making them safe
- making them predictable
- making them production-ready

Small Dockerfile decisions have large operational impact.

---

## Why this matters for DevOps

Modern DevOps is deeply connected with supply chain security.

Understanding:
- base images
- runtime composition
- vulnerability scanning
- minimal containers

is no longer optional.

It is required for production environments.

---

## Author

Tiago Franco  
DevOps Engineer — building and documenting in public.
