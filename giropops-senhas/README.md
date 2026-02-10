# 🔐 giropops-senhas — Container Hardening Case Study

This project demonstrates the evolution of a containerized Python application from a vulnerable and heavy image to a production-grade hardened container using distroless principles.

> ⚠️ This is not a tutorial repository.  
> This is a production-like container hardening exercise focused on DevSecOps practices.


The goal of this exercise was to simulate a real DevOps scenario:

> How would I ship this container securely to production?

---

# 🎯 Objectives

- Reduce image size
- Eliminate vulnerabilities
- Apply DevSecOps mindset
- Use secure base images
- Minimize attack surface
- Separate build and runtime properly

---

# 🧪 Initial Scenario (v1.0)

The initial container version reflected a common real-world scenario: 
a functional container image, but not optimized or hardened for production environments.

### Characteristics
- Large base image
- Included build tools
- High vulnerability count
- Large attack surface
- Not production ready

### Results

| Version | Size | Vulnerabilities |
|--------|------|----------------|
| v1.0 | ~415MB | Multiple HIGH/CRITICAL |

Security scan performed with **Trivy**.

---

# 🛠 Hardening Strategy

To transform this container into a production-grade image:

### 1. Multi-stage build
Separated build environment from runtime environment.

### 2. Virtualenv isolation
Dependencies installed inside isolated environment to avoid system pollution.

### 3. Chainguard distroless base image
Using Chainguard Wolfi-based images:

- Minimal runtime
- No package manager
- No unnecessary binaries
- Reduced attack surface
- Frequent security updates

### 4. Only runtime artifacts copied
Final image contains only:
- application
- virtualenv
- required assets

No build tools included.

---

# 🐳 Final Dockerfile strategy

- Stage 1: build dependencies using `chainguard python:latest-dev`
- Stage 2: minimal runtime using `chainguard python:latest`
- Copy only necessary artifacts
- Run using minimal runtime

---

# 📊 Final Results

| Version | Size | Vulnerabilities |
|--------|------|----------------|
| v1.0 | ~415MB | Several HIGH/CRITICAL |
| v4.0 hardened | ~31MB | 0 vulnerabilities |

Validated with:
- Trivy
- Docker Scout

---

# 🔐 Security Gains

- Minimal base image
- No shell in runtime
- No package manager
- Reduced attack surface
- Smaller SBOM
- Faster image pull
- Production-ready container

---

# 📁 Evidence

Security scans and evolution logs available in:

scans/


---

# 🧠 What this project demonstrates

This project reflects real DevOps engineering concerns:

- Container security
- Image optimization
- Supply chain awareness
- Production mindset
- Continuous improvement

---

# 🚀 Engineering Takeaways

This case study highlights how small container decisions can have major impact in:

- security posture
- image distribution speed
- runtime reliability
- production readiness

Container hardening is not about making things smaller only —  
it's about reducing risk.

---

# 👨‍💻 Author

Tiago Franco  
DevOps Engineer in progress — building and documenting in public.
