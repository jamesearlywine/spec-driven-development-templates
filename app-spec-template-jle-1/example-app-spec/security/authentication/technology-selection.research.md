# Authentication – Technology Selection (Research)

Options for auth: OAuth2/OIDC providers, libraries, session handling.

## Options

| Option | Pros | Cons |
|--------|------|-----|
| **AWS Cognito (OIDC)** | Managed, integrates with AWS; Hosted UI; JWKS for validation | AWS lock-in; customization limits |
| Auth0 | Rich features, many integrations | Cost at scale; vendor dependency |
| Keycloak | Self-hosted, flexible | Operate and maintain yourself |
| Custom OIDC | Full control | Build and secure yourself |

## Recommendation

**OIDC from Cognito.** Use Cognito user pool with OIDC; frontend uses Hosted UI or SDK; backend validates JWTs via Cognito JWKS. Details in technology-selection.spec.md.
