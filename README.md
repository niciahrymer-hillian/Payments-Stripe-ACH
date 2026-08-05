# Payments-Stripe-ACH

### Payments done properly: Stripe cards and ACH, idempotency, webhooks as the source of truth, refunds, and failure handling.

![Chain S](https://img.shields.io/badge/Chain%20S-0F766E?style=for-the-badge) [![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue?style=for-the-badge)](LICENSE-GPL) [![License: AGPL v3](https://img.shields.io/badge/License-AGPLv3-blue?style=for-the-badge)](LICENSE-AGPL)

[📖 Lesson Plan](docs/LESSON_PLAN.md)

<!-- SCREENSHOT PLACEHOLDER: docs/screenshots/overview.png -->

> ⬜ **Scaffold pending.** Directory created to portfolio standard; full content (README, lesson plan, tour + quiz, skeleton code) still to be built. Part of **Chain S — FinTech Engineering**.

## Why This Was Built

Taking money is the part of an application where sloppiness becomes expensive. A double-submitted form
must not double-charge. A client saying "payment succeeded" must never be trusted — only the provider's
webhook can confirm it. A refund has to reference the original charge and land back in the ledger correctly.

I also care about ACH specifically, not just cards. On a $50 fee, a card costs roughly $1.75 and ACH about
$0.40, and plenty of the fixed-income renters I've worked with don't hold a credit card at all. ACH isn't a
cost optimization in that context — it's access.

## Why This Matters (Industry Application)

Payments experience is one of the most directly monetizable backend skills there is, and the concepts —
idempotency keys, webhook verification, reconciliation, PCI scope — apply to every provider, not just
Stripe. Any company that charges customers needs someone who has thought carefully about the failure modes,
and those failure modes are the whole lesson.

## Topics Covered

| Area | What this project covers |
|------|--------------------------|
| Idempotency | Idempotency keys so a retry never charges twice |
| Webhooks | Signature verification, replay protection, and webhook-as-truth |
| ACH vs cards | Cost, settlement time, returns, and why ACH is an access issue |
| Refunds | Partial and full refunds referencing the original charge |
| PCI scope | Why card data must never touch your server (Elements/Checkout) |
| Reconciliation | Tying provider payouts back to your own ledger |

## How This Connects

Chain S (FinTech Engineering). Posts into **Double-Entry-Ledger**; the same seam pattern I use for payments in my Chain G work.

---
Dual licensed — [GPL v3](LICENSE-GPL) and [AGPL v3](LICENSE-AGPL).
