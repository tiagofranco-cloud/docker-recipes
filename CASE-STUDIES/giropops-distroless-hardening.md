# From 415MB to 31MB: Hardening a Python Container with Distroless

## Context

In real-world container environments, the main challenge is rarely functionality —  
it's security, efficiency and production readiness.

Many containers running in production today still ship:
- unnecessary packages
- large attack surface
- known vulnerabilities
- poor runtime separation

This case study documents the process of transforming a functional container image into a hardened, production-grade artifact using modern DevSecOps practices.

---

## Initial State

The original container image presented a common real-world scenario:

- ~415MB image size
- Multiple HIGH and CRITICAL vulnerabilities
- Build tools present in runtime
- Large and generic base image
- High attack surface
- Slow distribution and pull time

The container worked.  
But it was far from production-ready.

---

## Engineering Goals

The goal was not simply to reduce size.

The real objectives were:

- Reduce vulnerabilities to zero
- Minimize runtime footprint
- Apply DevSecOps mindset
- Adopt hardened base images
- Improve supply chain trust
- Simulate production-grade delivery standards

This project was approached as if the container would be deployed into a real production environment.

---

## Strategy

### Multi-stage build separation
Build and runtime environments were fully separated.

This ensures:
- build dependencies remain outside final image
- runtime stays minimal
- smaller SBOM
- reduced attack surface

### Python virtual environment isolation
Dependencies were installed inside an isolated virtual environment.

Benefits:
- predictable runtime behavior
- no system-level pollution
- controlled dependency scope

### Distroless Chainguard base image
The final runtime uses a Chainguard Wolfi-based Python image.

Key advantages:
- minimal operating system footprint
- continuously patched packages
- no package manager in runtime
- no shell available
- significantly reduced CVE exposure

Only runtime artifacts were copied into the final container.

---

## Final Results

| Metric | Before | After |
|-------|-------|------|
| Image size | ~415MB | ~31MB |
| Vulnerabilities | HIGH/CRITICAL present | 0 findings |
| Runtime footprint | Large | Minimal |
| Production readiness | Low | High |

Validated using:
- Trivy vulnerability scanner
- Docker Scout analysis

---

## Security Impact

Reducing container size is not just about performance.

It directly affects:

- CVE exposure surface
- SBOM complexity
- patching scope
- registry storage
- network transfer time
- deployment speed in clusters

A hardened container improves not only runtime security but the entire software delivery lifecycle.

---

## Lessons Learned

Container engineering goes beyond making applications run.

It requires ensuring they are:
- secure
- predictable
- observable
- production-ready

Small Dockerfile decisions can have significant operational and security impact.

Adopting hardened base images and minimal runtimes should be a default practice in modern DevOps workflows.

---

## Why This Matters for DevOps

Modern DevOps is deeply connected to software supply chain security.

Understanding:
- base image selection
- runtime composition
- vulnerability scanning
- minimal container strategies
- distroless principles

is no longer optional.

It is a fundamental requirement for production environments.

---

## Evidence

All data and security scans referenced in this case study are available:

- Image size comparison  
  `../giropops-senhas/scans/image-sizes.txt`

- Trivy scan — vulnerable version  
  `../giropops-senhas/scans/trivy-v1.0.txt`

- Trivy scan — hardened version  
  `../giropops-senhas/scans/trivy-v4.0.txt`

---

## Author

Tiago Franco  
DevOps Engineer — building and documenting in public.
