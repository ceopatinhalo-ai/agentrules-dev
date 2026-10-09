# Cloud & Docker DevOps Gatekeeper Standards
# Targets: Docker, Docker Compose, GitHub Actions CI/CD, Cloudflare, Production Guardrails

## 1. Container Packaging Principles
- Always use multi-stage Docker builds to keep images minimal (< 50MB for Go/Rust, < 150MB for Node/Python).
- Use pinned Alpine or Distroless official base images (`python:3.12-alpine`, `node:22-alpine`).
- Run application containers as non-root user (`USER nonroot` or `USER 10001:10001`).
- Never store secrets, `.env` files, or `.git` directories inside images (use `.dockerignore`).

## 2. Docker Compose & Local DX
- Define clear service dependency chains with `depends_on` and health checks (`test: ["CMD", "curl", "-f", "http://localhost:8000/health"]`).
- Map volumes only in development (`docker-compose.override.yml`), never in production.
- Use explicit network bridges to isolate internal databases from public web interfaces.

## 3. CI/CD GitHub Actions Pipeline
- Every Pull Request must pass the 4-gate verification:
  1. `Lint & Format`: Ruff / Biome / ESLint with zero warnings.
  2. `Security Scan`: Trivy or Grype for container vulnerabilities + GitGuardian for secrets.
  3. `Automated Tests`: Red-Green unit and integration tests with > 80% coverage.
  4. `Build Verification`: Container builds successfully without cache poisoning.

## 4. Zero-Downtime Deployment & Health Checks
- Expose standardized `/healthz` (liveness) and `/readyz` (readiness) endpoints.
- Deploy with rolling update or blue-green strategy. Never terminate older pods before new pods pass readiness probes.
- Enable automated database migration guards: migrations must be backward-compatible before new code deployment.
