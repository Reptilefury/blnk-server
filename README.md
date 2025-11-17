# BLNK Server - Cloud Run Deployment

Infrastructure as Code for BLNK Finance Wallet Server on Google Cloud Run.

## Overview

This repository manages the deployment of the BLNK finance wallet server to Google Cloud Run with:
- Internal ingress (accessible only via APISIX gateway)
- Supabase PostgreSQL database integration
- Redis caching on VM
- Automated CI/CD deployment

## Architecture

```
Internet → APISIX Gateway (VM) → Cloud Run (BLNK Server) → Supabase DB
                                      ↓
                                 Redis (VM)
```

## Access

- **Public API**: https://136.111.45.49:19080/ledgers
- **Direct Cloud Run**: Internal only (restricted)

## Deployment

Automatic deployment on push to `main` branch via GitHub Actions.

## Environment Variables

- `BLNK_DATA_SOURCE_DNS`: Supabase PostgreSQL connection
- `BLNK_REDIS_DNS`: Redis server on VM
- `BLNK_SERVER_PORT`: Service port (5001)
