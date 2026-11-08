# Deployment Guide

## Prerequisites
- Docker Engine
- Docker Compose plugin
- An isolated Linux VM
- Sufficient memory and disk for the containers

## Start
```bash
docker compose pull
docker compose up -d
docker compose ps
```

Open `http://127.0.0.1:8080` from the same VM.

## Logs
```bash
docker compose logs --tail=200 waf
docker compose logs --tail=100 juice-shop
```

The official CRS container image supports environment variables such as `BACKEND`, `PORT`, `MODSEC_RULE_ENGINE` and `BLOCKING_PARANOIA`. Confirm current image documentation before relying on any additional setting.

## Switch to blocking mode
After collecting detection-only evidence, change:

```yaml
MODSEC_RULE_ENGINE: DetectionOnly
```

to:

```yaml
MODSEC_RULE_ENGINE: On
```

Then recreate the WAF container:

```bash
docker compose up -d --force-recreate waf
```

Retest benign and malicious-pattern traffic. Do not assume every sample request must be blocked; record the actual CRS match and response.

## Stop and clean up
```bash
docker compose down
```

To remove containers and the network without deleting images:
```bash
docker compose down
```
