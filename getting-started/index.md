# Getting Started

## Requirements

- Docker + Docker Compose
- AWS SES credentials
- Polar organization ID (for license validation)

## Quick Start

```bash
cp .env.example .env
docker compose up -d
```

Then open the app and complete setup:

1. Create initial admin at `/setup`
2. Activate license at `/activate`
3. Configure SES in `/app/settings`
