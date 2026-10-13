# Agent Evidence Check

Independent evidence receipts for AI agent actions, payments and workflow execution.

## Why this exists

AI agents are starting to execute real workflows: payments, refunds, invoice reconciliation, marketplace actions, escrow releases, API operations and business automations.

The weak point is evidence. A green log is often treated as proof, even when:

- a tool returned `success` but the external system did not change;
- a timeout created duplicate retries;
- an approval expired before the effect happened;
- an agent verified its own work;
- a receipt was signed but the decoder/schema changed later;
- a workflow claimed zero activity without proving the observer was alive.

Agent Evidence Check turns one decisive workflow claim into a small evidence pack that can be inspected, replayed or challenged.

Core principle:

> Unknown is not green.

## What it checks

For each claim, the project records:

- the action the agent claimed to perform;
- the command or intent that was issued;
- the remote acknowledgement;
- the observed external effect;
- an independent readback or witness where possible;
- authorization state at the time of effect;
- retry grouping and logical event identity;
- runtime/plugin/memory evidence;
- explicit gaps and failure vocabulary.

The result should not be just pass/fail. It should distinguish:

- `pass`
- `pass_with_flags`
- `unknown`
- `unverified`
- `partial`
- `blocked`

## Crypto / payment fit

Crypto workflows are a strong fit because actions may be financial, irreversible, asynchronous or spread across on-chain and off-chain systems.

The first target is a false-green payment/workflow receipt:

1. An agent claims that an invoice was paid and archived.
2. Internal logs look green.
3. External readback shows that the payment is still pending or unverified.
4. The receipt is marked `blocked` or `unknown`, not green.

The model is chain-agnostic. Ethereum L1 is used as a reference environment; Base and other EVM chains can be integrated through readback adapters, transaction identifiers and explorer/API verification.

## Current status

This is an early Colosseum submission prototype. It packages prior internal research around Invoice Evidence Check and Workflow Evidence Audit into a public, crypto-oriented product direction.

No production wallets, private credentials or real customer data are included.

## Next steps

- Add a runnable validator for the receipt schema.
- Add external readback adapters for EVM transaction/payment state.
- Add a demo script for a false-green payment receipt.
- Add runtime and memory evidence fields for agentic workflows.
- Produce a short video demo.
