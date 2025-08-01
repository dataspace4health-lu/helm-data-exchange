# REST API Component

This component provides the REST API service for data delivery.

## Configuration

| Parameter | Description | Default |
|-----------|-------------|---------|
| `enabled` | Enable the component | `true` |
| `replicaCount` | Number of replicas | `1` |
| `image.repository` | Image repository | `ds4h-registry:5432` |
| `image.name` | Image name | `rest-service/rest-api` |
| `image.tag` | Image tag | `latest` |
| `service.port` | Service port | `3000` |
| `config.environment` | Environment | `production` |
| `config.api.basePath` | API base path | `/api` |

## Health Checks

The service provides health check endpoints:
- `/health` - Basic health check

## Building

```bash
make build
```
