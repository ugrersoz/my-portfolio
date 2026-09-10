# Security

Report vulnerabilities privately using the email contact on the [website](https://ugrersoz.github.io/#contact). If GitHub private vulnerability reporting is enabled, you may also use [a private advisory](https://github.com/ugrersoz/ugrersoz.github.io/security/advisories/new). Do not include credentials or personal data in public issues.

This is a public, static portfolio. It has no login, backend, analytics, or visitor database. Published contact details and media are public and can be copied. GitHub operates the hosting infrastructure.

Never commit credentials, private documents, or original personal datasets. Google ownership verification files are intentionally public and must remain deployed. If a credential is exposed, revoke or rotate it first; deleting a file does not remove it from Git history, forks, or existing copies.

Only the current `main` version is maintained. Automated checks validate public assets and browser policy before publishing. The deployment uses pinned actions and explicitly selected public paths.

The browser policy limits scripts to this site's files and blocks connections, embedded frames, plugins, and form submissions. GitHub Pages does not provide repository-configurable response headers; HTML metadata cannot enforce `frame-ancestors`, `Permissions-Policy`, or `X-Content-Type-Options`. Do not treat it as protection against all attacks or scraping.
