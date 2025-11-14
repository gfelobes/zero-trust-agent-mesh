# Zero-Trust Agent Mesh

A Kubernetes + Istio example showing how to enforce mTLS and RBAC between agent services in a zero-trust mesh.

## Features

- Three FastAPI services: A, B, and C
- Istio-based mTLS between all services
- Authorization policies allowing A→B and blocking C→B
- Automatic certificate issuance and rotation
- Example of service-level isolation for tenants

## Tech Stack

- Kubernetes
- Istio / Envoy
- FastAPI
- Docker

## Getting Started

1. Deploy Istio or use an Istio-enabled cluster.
2. Apply manifests in `k8s/`.
3. Port-forward service A or B to test calls.

## Demo Scenario

- Call B from A: request succeeds.
- Call B from C: request is denied by Istio AuthorizationPolicy.
- Show mTLS metrics in Istio dashboard (Kiali/Grafana).

## Design Notes

See `docs/architecture.md` and `docs/mtls-config.md` for the security model and policies.




### 📁 Structure
```bash
zero-trust-agent-mesh/
├─ services/
│  ├─ service_a/
│  │  ├─ main.py
│  │  └─ Dockerfile
│  ├─ service_b/
│  │  ├─ main.py
│  │  └─ Dockerfile
│  └─ service_c/
│     ├─ main.py
│     └─ Dockerfile
├─ k8s/
│  ├─ namespace.yaml
│  ├─ deployment-a.yaml
│  ├─ deployment-b.yaml
│  ├─ deployment-c.yaml
│  ├─ istio-gateway.yaml
│  ├─ destination-rules.yaml
│  └─ authorization-policies.yaml
├─ docs/
│  ├─ architecture.md
│  └─ mtls-config.md
├─ README.md
└─ requirements.txt
