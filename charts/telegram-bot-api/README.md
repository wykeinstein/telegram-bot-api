# telegram-bot-api Helm Chart

This chart deploys a self-hosted [Telegram Bot API server](https://github.com/tdlib/telegram-bot-api).

## Prerequisites

- Kubernetes 1.23+
- Helm 3.8+
- Telegram `api_id` and `api_hash`

## Install

```bash
helm install bot-api ./charts/telegram-bot-api \
  --set-string telegram.apiId=<your_api_id> \
  --set-string telegram.apiHash=<your_api_hash>
```

## Uninstall

```bash
helm uninstall bot-api
```

## Configuration

| Key | Type | Default | Description |
| --- | --- | --- | --- |
| `replicaCount` | int | `1` | Number of replicas when autoscaling is disabled. |
| `image.repository` | string | `ghcr.io/aiogram/telegram-bot-api` | Container image repository. |
| `image.tag` | string | `latest` | Container image tag. |
| `service.type` | string | `ClusterIP` | Kubernetes service type. |
| `service.port` | int | `8081` | HTTP port exposed by the service and container. |
| `telegram.apiId` | string | `""` | Telegram API ID (required). |
| `telegram.apiHash` | string | `""` | Telegram API hash (required). |
| `extraArgs` | list | `[]` | Additional CLI flags for `telegram-bot-api`. |
| `extraEnv` | list | `[]` | Additional container env vars. |
| `persistence.enabled` | bool | `true` | Enables persistent data volume. |
| `persistence.size` | string | `5Gi` | PVC size request. |
| `autoscaling.enabled` | bool | `false` | Enable HorizontalPodAutoscaler. |
