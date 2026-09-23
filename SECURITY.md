# Security Policy

## Reporting a vulnerability

Please do not disclose suspected vulnerabilities, credentials, exploit details, or sensitive reproduction data in a public issue.

This repository does not currently advertise a dedicated private vulnerability-reporting channel. Until one is enabled, open a minimal issue that asks the maintainers for a private security contact without including technical details that could enable exploitation. A maintainer can then move the discussion to an appropriate private channel.

When reporting privately, include the affected version or commit, impact, reproduction steps, and a minimal proof of concept when it is safe to do so.

## Secret handling

Never commit live credentials, API keys, access tokens, private keys, session cookies, or production secrets. Use environment variables and the example environment files for configuration.

The repository uses `detect-secrets` in pre-commit and CI. The baseline exists only to record reviewed historical findings; it must not be used to suppress a newly introduced real secret.

If a finding is an intentional non-secret fixture or placeholder, prefer changing the fixture so it is obviously synthetic. Use a targeted allowlist only when the value cannot reasonably be mistaken for a usable credential.

## Canary tokens

Do not commit live canary tokens or honey credentials to this repository. A canary token is still an active credential-like value and may disclose monitoring metadata or trigger external systems when accessed.

Documentation and tests should use clearly inert placeholders such as `CANARY_TOKEN_EXAMPLE`. If a security test requires a live canary, provision it outside the repository, inject it at runtime through the environment or CI secrets, and revoke it after the test.
