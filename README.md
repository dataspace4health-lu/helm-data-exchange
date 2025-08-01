# Helm Data Exchange

This Helm chart deploys the REST Data Delivery service for data infrastructure federation, providing REST API endpoints for data exchange operations.

## Prerequisites

- Kubernetes 1.19+
- Helm 3.0+

## Installation

1. Update chart dependencies:
```bash
helm dependency update
```

2. Install the chart:
```bash
helm install rest-service .
```

Or with custom values:
```bash
helm install rest-service . -f custom-values.yaml
```

## Uninstallation

```bash
helm uninstall rest-service
```

## Configuration

The following table lists the configurable parameters and their default values.

| Parameter | Description | Default |
|-----------|-------------|---------|
| `rest-api.enabled` | Enable REST API component | `true` |
| `rest-api.replicaCount` | Number of replicas | `1` |
| `rest-api.image.repository` | Image repository | `ds4h-registry:5432` |
| `rest-api.image.name` | Image name | `data-delivery-service` |
| `rest-api.image.tag` | Image tag | `latest` |
| `rest-api.service.port` | Service port | `3000` |
| `rest-api.config.environment` | Environment (development, staging, production) | `development` |
| `rest-api.config.api.baseUrl` | API base URL | `https://dataspace4health.local` |
| `rest-api.config.api.basePath` | API base path | `/rest-api/v1` |
| `rest-api.config.oidcIssuer` | OIDC issuer URL | `""` |
| `rest-api.config.oidcClientId` | OIDC client ID | `""` |
| `rest-api.ingress.enabled` | Enable ingress | `true` |

## Components

### rest-api
The main REST API service that provides data delivery functionality with:
- RESTful endpoints for data exchange operations
- OIDC authentication and authorization
- Configurable API base path and URLs

## Development

### Uninstalling

```bash
make uninstall
```

### Cleaning Up

```bash
make clean
```

### Building

```bash
make build
```

### Testing (There are no tests defined currently)

```bash
make test
```

### Installing

```bash
make install
```

### Available Make Commands

- `make all` - Build, install, test, uninstall, and clean
- `make build` - Build the Helm chart and package dependencies
- `make install` - Install the chart using packaged version
- `make test` - Run Playwright end-to-end tests
- `make uninstall` - Uninstall the chart and cleanup
- `make clean` - Remove build artifacts
