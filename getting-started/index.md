# Getting Started

## Requirements

- Docker + Docker Compose
- AWS SES credentials

## Quick Start

```bash
cp .env.example .env
docker compose up -d
```

Then open the app and complete setup:

1. Create initial admin at `/setup`
2. Activate license at `/activate`
3. Configure organization SES credentials in `/app/organization`

## Environment

Self-hosted `.env` should include:

```env
NODE_ENV=development
COOKIE_SECRET=change-me-to-a-long-random-value
DB_SECRET_KEY=base64-encoded-32-byte-key
DATABASE_URL=postgres://postgres:postgres@localhost:5433/ses_ui
APP_BASE_URL=http://localhost:3000
SES_WEBHOOK_URL=
SES_WEBHOOK_SECRET=
```

- `SES_WEBHOOK_URL` can be left empty to use `${APP_BASE_URL}/api/webhooks/ses`
- `SES_WEBHOOK_SECRET` is required to authenticate webhook calls

## AWS Permissions

For full functionality, use:

- SES template + send permissions (SESv2 + SES)
- `ses:GetSendQuota`
- `cloudwatch:GetMetricData` (dashboard deliverability)
- AWS managed policy `AmazonSNSFullAccess` (for webhook setup automation)

Optional hardening:

- Replace `AmazonSNSFullAccess` with a custom SNS policy limited to:
  `CreateTopic`, `Subscribe`, `SetTopicAttributes`, `ListSubscriptionsByTopic`
