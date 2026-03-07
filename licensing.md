# Licensing

Template Pilot uses org-level license activation.

- One activation per org/deployment
- Revalidation runs automatically on interval
- Invalid/revoked licenses are revoked in-app

Configure:

```env
POLAR_ORGANIZATION_ID=...
POLAR_ENV=production
POLAR_VALIDATE_INTERVAL_SECONDS=300
```
