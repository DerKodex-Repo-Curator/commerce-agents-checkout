# Support

## Before asking for help

The fastest path is usually the repository documentation:

- [integration guide](docs/integration.md) for backend wiring and checkout
  handoff behavior;
- [testing guide](docs/testing.md) for local and contract validation; and
- [security documentation](docs/security.md) for the boundary between this
  adapter, the seller backend, and Mercado Pago.

## Bugs, documentation, and integration questions

Use the matching public GitHub issue form for reproducible bugs, documentation
corrections, integration questions, and focused feature proposals. Include the
package and Python versions when relevant, a minimal sanitized reproduction,
the expected behavior, and the observed behavior. Do not include credentials,
shopper data, session IDs, Order IDs, seller references (including
`external_reference`), idempotency keys, complete checkout URLs, or other
sensitive values.

## Security concerns

Do not report vulnerabilities in a public issue, pull request, or discussion.
Follow the private reporting process in [SECURITY.md](SECURITY.md).

## Conduct concerns

For a concern about participation in the project, use the private channel
described in the [Code of Conduct](CODE_OF_CONDUCT.md).

## Account and payment-product support

Questions about a Mercado Pago account, live payments, or the hosted checkout
experience belong to
[Mercado Pago Developer Support](https://www.mercadopago.com/developers/en/support/center).
This repository cannot access or troubleshoot an individual seller account.
