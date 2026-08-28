# Security Policy

## Scope

This repository contains only Markdown instructions and JSON manifests (no executable code, no server, no dependencies) — it teaches AI coding agents how to consume the [Zeep Orbit](https://github.com/zeeplabs/zeep-orbit) API and SDKs. Traditional vulnerability classes (RCE, injection, auth bypass) don't apply here.

What we still treat as a security-relevant report:

- Instructions in a `SKILL.md`/reference file that would lead an agent to produce insecure integration code (e.g. encouraging insecure token storage, disabling auth checks, bypassing RLS expectations)
- Content that's inaccurate in a way that could cause a real security issue downstream (wrong auth flow, wrong permission model description)

For vulnerabilities in Zeep Orbit itself (the product this skill documents), report against the [zeep-orbit repository's security policy](https://github.com/zeeplabs/zeep-orbit/blob/main/SECURITY.md) instead — this repo has no control over the product's actual implementation.

## Reporting

Please **do not** open public issues for security-relevant reports.

Send a private report to **security@zeeptecnologia.com.br** or reach out to the maintainers directly.

You can expect:

- Acknowledgment within 48 hours
- Regular updates on the fix progress
- Credit upon disclosure (if desired)
