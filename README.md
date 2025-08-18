# Helm Data Exchange

This Helm chart deploys the Data Provision Service (DPS) for data infrastructure federation, providing REST API endpoints for data exchange operations.

**Chart Version:** 1.0.0  
**App Version:** 1.0.0

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
helm install data-exchange .
```

Or with custom values:
```bash
helm install data-exchange . -f custom-values.yaml
```

## Chart Structure

This chart uses a dependency-based structure:
- **Main chart**: `data-exchange` - The umbrella chart that orchestrates the deployment
- **Dependency**: `dps` - The Data Provision Service component located in `components/dps/`

## Uninstallation

```bash
helm uninstall data-exchange
```

## Configuration

The following table lists some of the configurable parameters and their default values.

| Parameter | Description | Default |
|-----------|-------------|---------|
| `dps.enabled` | Enable DPS component | `true` |
| `dps.replicaCount` | Number of replicas | `1` |
| `dps.image.repository` | Image repository | `ds4h-registry:5432` |
| `dps.image.name` | Image name | `data-provision` |
| `dps.image.tag` | Image tag | `latest` |
| `dps.service.port` | Service port | `3000` |
| `dps.config.environment` | Environment (development, staging, production) | `production` |
| `dps.config.api.baseUrl` | API base URL | `https://dataspace4health.local` |
| `dps.config.api.basePath` | API base path | `/data/api/v1` |

## Components

### dps (Data Provision Service)
The main Data Provision Service that provides data delivery functionality with:
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

### Testing

The chart includes Playwright end-to-end tests. Test results are stored in timestamped directories under `tests/results/`.

```bash
make test
```

Note: Tests run in a Docker container using `mcr.microsoft.com/playwright:v1.46.1`.

### Installing

```bash
make install
```

### Available Make Commands

- `make all` - Build, install, test, uninstall, and clean
- `make build` - Build the Helm chart and package dependencies  
- `make install` - Install the chart using packaged version as `dps`
- `make test` - Run Playwright end-to-end tests
- `make uninstall` - Uninstall the chart and cleanup
- `make clean` - Remove build artifacts
