# Authentication Spec

End-to-end authentication behavior for Task Tracker using OIDC from Cognito.

## Flows

- **Login**: User is redirected to Cognito Hosted UI (or equivalent); after successful auth, Cognito redirects back with authorization code (or tokens); app exchanges code for tokens and stores them. Optional: use Cognito SDK (e.g. Amplify) for embedded flows.
- **Logout**: Revoke refresh token if applicable; clear local tokens; optionally redirect to Cognito logout endpoint for global sign-out.
- **Session refresh**: Use refresh token to obtain new ID and access tokens before expiry; backend accepts valid access tokens only (no refresh on backend).

## Requirements

- **Password policy**: As configured in Cognito user pool (e.g. complexity, minimum length).
- **MFA**: Optional; configure in Cognito (SMS, TOTP) if required.
- **Account lockout**: Cognito policies (e.g. failed attempt lockout); document in security-controls.spec.md if needed.
