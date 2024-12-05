# Multi-Tenant Service Mesh Helm Chart

This Helm chart implements a multi-tenant service mesh environment with comprehensive isolation and security features.

## Features

- Tenant isolation at network and resource level
- Automated creation of tenant-specific policies
- mTLS support
- Dynamic RBAC policies
- Resource quotas per tenant
- Istio virtual services and gateways

## Prerequisites

- Kubernetes 1.19+
- Helm 3.0+
- Istio 1.18+ (or Linkerd)

## Installation

```bash
helm repo add istio https://istio-release.storage.googleapis.com/charts
helm dependency update
helm install multi-tenant-mesh ./multi-tenant-mesh
```

## Configuration

See values.yaml for detailed configuration options. Key parameters include:

- `tenants`: List of tenant configurations
- `serviceMesh`: Service mesh provider and global settings
- `rbac`: RBAC settings
- `resourceQuotas`: Resource quota configurations

## Adding a New Tenant

Add a new tenant configuration in values.yaml:

```yaml
tenants:
  - name: new-tenant
    namespace: new-tenant
    labels:
      tenant: new-tenant
    networkPolicies:
      enabled: true
    istio:
      mtls:
        mode: STRICT
```

## Security Features

- Network isolation between tenants
- mTLS communication
- RBAC policies
- Resource quotas
- Authorization policies

## License

MIT
