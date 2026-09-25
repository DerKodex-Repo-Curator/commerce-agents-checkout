# Contributing

Thanks for considering a contribution to `mercadopago-commerce-agents-checkout`.
This project turns an agent-supplied cart, verified against a seller-controlled
trusted catalog, into a Checkout Pro Order handoff for a commerce-agents
backend. Changes should preserve that security boundary.

Please follow the [Code of Conduct](CODE_OF_CONDUCT.md) in every project space.

## Before opening an issue

- For a vulnerability or suspected exposure of payment, credential, or shopper
  data, use the private path in [SECURITY.md](SECURITY.md). Do not open a public
  issue.
- For installation and integration questions, start with the
  [integration guide](docs/integration.md) and [support guide](SUPPORT.md). If
  those do not resolve the question, use the integration or documentation help
  issue form with sanitized information.
- For reproducible bugs, documentation corrections, or focused improvements,
  search existing issues first and then use the appropriate issue template.

## Development setup

The supported development baseline is Python 3.11 or later.

```bash
python -m venv .venv
. .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -e .
python -m pip install pylint==4.0.7 isort==8.0.1
```

Run the same core checks expected by continuous integration before opening a
pull request:

```bash
python -m unittest discover -s tests
pylint --max-line-length=100 src/mercadopago_commerce_agents examples
isort --check-only --diff src tests examples
```

The contract test has an upstream dependency and is documented separately in
[docs/testing.md](docs/testing.md). Do not change the reviewed upstream pin as
part of an unrelated contribution.

## Making a change

1. Fork the repository and create a focused branch from `main`.
2. Keep each pull request scoped to one problem. Include tests when behavior
   changes, and update public documentation when the integration contract
   changes.
3. Never add Access Tokens, real checkout URLs, buyer data, session IDs, Order
   IDs, seller references (including `external_reference`), or idempotency keys
   to commits, test fixtures, logs, or screenshots.
4. Explain the problem, approach, validation, and any compatibility impact in
   the pull request description.
5. Respond to review feedback and keep the branch current with `main` when
   requested.

## Design and security expectations

This package deliberately keeps payment authority outside of model-authored
data. Contributions must preserve the existing invariants:

- prices, currency, stock, and item titles come from the seller's trusted
  catalog, not the cart supplied by an agent;
- a seller backend owns attempt persistence, webhook validation, reconciliation,
  authentication, and fulfillment;
- an inconclusive Order operation must not silently release a fallback checkout;
  and
- credentials and sensitive checkout data must not reach the model or logs.

See [docs/security.md](docs/security.md) for the full responsibility split.

## Licensing

By contributing, you agree that your contribution is provided under the
[Apache License 2.0](LICENSE).
