# 📖 Lesson Plan — Payments-Stripe-ACH

> **Chain S — FinTech Engineering** | Payments done properly: Stripe cards and ACH, idempotency, webhooks as the source of truth, refunds, and failure handling.

## What This Project Is

Integrate card and ACH payments properly — idempotency, webhook-verified settlement, refunds, and reconciliation into a ledger.

## Learning Objectives

By the end I can:

1. Create charges with an **idempotency key** so retries never double-charge.
2. Verify **webhook signatures** and treat the webhook as the source of truth.
3. Explain the cost, timing, and return differences between cards and ACH.
4. Issue partial and full refunds referencing the original charge.
5. Keep card data off your server and out of PCI scope.
6. Reconcile provider payouts against your own ledger.

## Software You Will Use

- Stripe test mode + SDK.
- Stripe Elements or Checkout on the frontend.
- A local tunnel (Stripe CLI / ngrok) for webhooks.
- PostgreSQL.

## Build Order

1. Create a PaymentIntent server-side; collect card details with Elements.
2. Add an idempotency key; replay the request and prove no double charge.
3. Receive and signature-verify the webhook; only then mark the charge cleared.
4. Enable ACH and compare cost and settlement time.
5. Implement refunds and post them to the ledger.
6. Reconcile a payout against your recorded transactions.

## Common Mistakes to Avoid

- Trusting the client's 'payment succeeded' instead of the webhook.
- Omitting idempotency keys and double-charging on a retry.
- Skipping webhook signature verification, so anyone can forge settlement.
- Letting card numbers touch your server and pulling yourself into PCI scope.
- Assuming ACH settles instantly, or ignoring returns days later.

## Check Your Understanding

The quiz covers idempotency keys, webhook signature verification, why client confirmation is untrustworthy, and card vs ACH tradeoffs.

## Why This Matters (Industry Application)

Payments experience is one of the most directly monetizable backend skills there is, and the concepts —
idempotency keys, webhook verification, reconciliation, PCI scope — apply to every provider, not just
Stripe. Any company that charges customers needs someone who has thought carefully about the failure modes,
and those failure modes are the whole lesson.

## Reflection Questions

- Which of your users cannot pay by card, and what does that mean for who your product actually serves?
- What happens to a resident's ledger when an ACH payment is returned a week later?
