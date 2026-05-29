# k8s-homelab

Kubernetes manifests for my personal homelab cluster, managed declaratively via ArgoCD.

## Structure

```
apps/
├── sealed-secrets/        # Bitnami Sealed Secrets controller
├── cert-manager/          # TLS certificate automation
├── metallb/               # Bare-metal LoadBalancer
├── envoy-gateway/         # Gateway API implementation
├── cloudflared/           # Cloudflare Tunnel ingress
├── longhorn/              # Distributed block storage
├── coredns/               # In-cluster DNS configuration
├── cloudnativepg/         # PostgreSQL operator
├── plugin-barman-cloud/   # CNPG backup plugin for S3
├── zot/                   # OCI container registry
├── keiba-db/              # PostgreSQL cluster (CNPG)
├── keiba-api/             # Backend API
├── bakepyon-ui/           # Frontend UI
└── writefreely/           # Personal blog
```

Each directory contains an ArgoCD `Application` manifest plus the Helm values
or raw Kubernetes manifests that ArgoCD syncs to the cluster.

## Secrets

Secrets are managed exclusively via [Sealed Secrets](https://github.com/bitnami-labs/sealed-secrets).
`*-sealedsecret.yaml` files contain ciphertext that only the cluster controller
can decrypt, so they are safe to commit.

## License

MIT — see [LICENSE](./LICENSE).
