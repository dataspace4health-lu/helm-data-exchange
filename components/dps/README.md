# Data Provision Service Component

This component provides the REST API service for data provisioning.

## Configuration

| Parameter | Description | Default |
|-----------|-------------|---------|
| `enabled` | Enable the component | `true` |
| `replicaCount` | Number of replicas | `1` |
| `image.repository` | Image repository | `ds4h-registry:5432` |
| `image.name` | Image name | `data-provision-service` |
| `image.tag` | Image tag | `latest` |
| `service.port` | Service port | `3000` |
| `config.environment` | Environment | `production` |
| `config.api.basePath` | API base path | `/data/api/v1` |
| `config.oidcBearerRealm` | Bearer realm for WWW-Authenticate header | `ds4h` |

## Health Checks

The service provides health check endpoints:
- `/health` - Basic health check

## Building

```bash
make build
```
