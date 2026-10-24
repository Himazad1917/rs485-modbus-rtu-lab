# Security Policy

## Scope
This repository contains public educational documentation and illustrative examples. It is not a production service and does not accept sensitive data.

## Reporting a concern
If you believe you found a security issue in this repository, please contact the repository owner through the contact options on the [GitHub profile](https://github.com/Himazad1917). Do not include credentials, personal data, customer information, or exploit details in a public issue.

## Secret handling
- Never commit API keys, passwords, access tokens, private keys, LoRaWAN application keys, customer records, or proprietary configuration.
- If a credential is exposed, revoke or rotate it immediately; deleting a file alone does not invalidate it or remove it from Git history.
- Use environment variables or an approved secret manager for real deployments.

## Scope limits
No production deployment, formal security certification, or full Git-history secret scan is implied by this document.