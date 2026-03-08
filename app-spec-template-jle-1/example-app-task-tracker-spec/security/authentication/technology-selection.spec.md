# Authentication – Technology Selection (Spec)

Chosen auth technology and integration approach for Task Tracker.

## Selected approach

- **Provider**: AWS Cognito (user pool)
- **Protocol**: OIDC (OpenID Connect)
- **Tokens**: ID token + access token (JWT); refresh token for session extension
- **Session**: Frontend stores tokens (e.g. memory + refresh in httpOnly cookie, or secure storage per platform)

## Integration points

- **Frontend**: Redirect to Cognito Hosted UI (or use Amplify/Cognito SDK); receive tokens; attach access token to API requests (e.g. Authorization: Bearer &lt;token&gt;).
- **Backend**: Validate JWT (signature, issuer, audience, expiry) using Cognito JWKS; extract identity and claims for authorization.
