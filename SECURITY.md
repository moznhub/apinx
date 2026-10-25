# Security policy

## Reporting a vulnerability

Please do **not** open a public issue or discussion for a security problem.

Use GitHub's private reporting instead:
[Report a vulnerability](https://github.com/moznhub/apinx/security/advisories/new). Or write
to [support@moznhub.com](mailto:support@moznhub.com) with "Security" in the subject.

Include what you can:

- the Apinx version (**Admin › About**, or `apinx version`) and the edition (on premises or Cloud);
- the steps to reproduce, and what an attacker gains;
- any proof of concept, logs or request IDs (remove secrets and personal data first).

We confirm receipt within **3 working days**, keep you informed while we work on a fix, and
credit you in the release notes if you wish. Please give us reasonable time to release a fix
before you disclose anything.

## Supported versions

Security fixes are released for the latest minor version. Apinx Cloud is updated by MoznHub;
on-premises customers with an active maintenance period receive the fix from MoznHub.

| Version | Security fixes |
|---|---|
| 1.1.x | Yes |
| 1.0.x | Upgrade to 1.1.x |

## Testing

Test only installations you own, or Apinx Cloud organizations you own. Do not run load tests,
denial-of-service tests or automated scanners against Apinx Cloud (`apinx.io` and its
subdomains), and do not access or change data that is not yours.
