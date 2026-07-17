# Security policy

## Reporting a vulnerability

Report security issues privately to [support@socq.ai](mailto:support@socq.ai).
Do not open a public GitHub issue for a suspected vulnerability or exposed
credential.

Please include a concise description, the affected repository and path,
reproduction steps with placeholder values, and redacted request or response
shapes where useful.

## Never publish

- SocQ API keys, bearer tokens, session tokens, or OAuth credentials
- Real customer data, account data, billing data, or production task payloads
- Private social account data or credentials for third-party platforms
- Internal hosts, proxy settings, service topology, or service secrets
- Callback URLs containing secrets or internal routes
- Unredacted logs, screenshots, or fixtures containing sensitive values

SocQ public repositories contain integration examples only. They must not store
private product source code or production configuration.
