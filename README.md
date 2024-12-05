# 🌐 Multi-Tenant Service Mesh Helm Chart

[![Helm](https://img.shields.io/badge/helm-v3.0.0+-blue.svg)](https://helm.sh)
[![Kubernetes](https://img.shields.io/badge/kubernetes-v1.19+-blue.svg)](https://kubernetes.io)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Istio](https://img.shields.io/badge/istio-1.18+-blue.svg)](https://istio.io)

> A powerful Helm chart for managing secure, isolated multi-tenant environments in Kubernetes service meshes (Istio/Linkerd).

<p align="center">
  <img src="https://raw.githubusercontent.com/cncf/artwork/master/projects/kubernetes/icon/color/kubernetes-icon-color.svg" width="100" />
  <img src="https://raw.githubusercontent.com/cncf/artwork/master/projects/helm/icon/color/helm-icon-color.svg" width="100" />
  <img src="https://raw.githubusercontent.com/cncf/artwork/master/projects/istio/icon/color/istio-icon-color.svg" width="100" />
</p>

## 🌟 Features

- 🔒 **Complete Tenant Isolation**
  - Network-level segregation
  - Resource quotas
  - Namespace isolation

- 🔐 **Enterprise-Grade Security**
  - Mutual TLS (mTLS) enforcement
  - Dynamic RBAC policies
  - Authorization policies

- 🚀 **Automated Management**
  - Policy generation
  - Virtual service creation
  - Gateway configuration

- 📊 **Resource Management**
  - CPU/Memory quotas
  - Network policies
  - Service mesh resources

## 📋 Prerequisites

Before you begin, ensure you have:

- Kubernetes cluster (v1.19+)
- Helm (v3.0.0+)
- Istio (v1.18+) or Linkerd installed
- `kubectl` configured to access your cluster

## 🚀 Quick Start

### 1. Add the Istio Repository
```bash
helm repo add istio https://istio-release.storage.googleapis.com/charts
```

### 2. Update Dependencies
```bash
helm dependency update
```

### 3. Install the Chart
```bash
helm install multi-tenant-mesh ./multi-tenant-mesh
```

## 🛠️ Configuration

### Basic Configuration
```yaml
# values.yaml
tenants:
  - name: tenant1
    namespace: tenant1
    labels:
      tenant: tenant1
    networkPolicies:
      enabled: true
```

### Advanced Settings

<details>
<summary>Click to expand</summary>

```yaml
serviceMesh:
  enabled: true
  provider: istio
  mtls:
    enabled: true
  monitoring:
    enabled: true
  tracing:
    enabled: true

resourceQuotas:
  enabled: true
  default:
    requests.cpu: "1"
    requests.memory: 1Gi
```
</details>

## 🔧 Components

| Component | Description |
|-----------|-------------|
| Namespace | Isolated tenant workspace |
| NetworkPolicy | Network-level isolation |
| AuthorizationPolicy | Access control rules |
| ResourceQuota | Resource limitations |
| VirtualService | Traffic routing rules |

## 🔍 Monitoring & Debugging

### Verify Installation
```bash
helm test multi-tenant-mesh
```

### Check Tenant Status
```bash
kubectl get ns,networkpolicy,resourcequota -l tenant=tenant1
```

## 📚 Examples

### Creating a New Tenant

<details>
<summary>Example Configuration</summary>

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
</details>

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

1. Fork the repository
2. Create your feature branch
3. Submit a pull request

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙋‍♂️ Support

- 📧 [Report an Issue](https://github.com/yashodhan271/Multi-tenant-service-mesh-Helm-chart/issues)
- 💬 [Discussion Forum](https://github.com/yashodhan271/Multi-tenant-service-mesh-Helm-chart/discussions)

## 🌟 Star History

[![Star History Chart](https://api.star-history.com/svg?repos=yashodhan271/Multi-tenant-service-mesh-Helm-chart&type=Date)](https://star-history.com/#yashodhan271/Multi-tenant-service-mesh-Helm-chart&Date)

---

<p align="center">
Made with ❤️ by the community
</p>
