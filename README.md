<p align="center">
  <img src="docs/hero.svg" width="100%" alt="Azure's billing and support UI leads to dead ends; these notes trace the one path that reaches what you wanted.">
</p>

<h1 align="center">azure-help</h1>

<p align="center"><b>Hard-won playbooks for the non-obvious corners of Azure.</b> Things in the Azure portal that turned out to be painful, inconsistent or flaky — written down so they don't have to be rediscovered from scratch.</p>

---

## Why this exists

Azure's billing and support flows are occasionally inconsistent enough that it's worth recording the **exact working steps** rather than relearning them each time. These notes come from filing real requests, dead ends included.

## In here

### 💸 Requesting a refund / credit

<p align="center">
  <img src="docs/refund-flow.svg" width="100%" alt="Four steps: find the invoice, try the self-service refund tool (hidden expedited-refund limit), file a billing support ticket as a credit request (skip the Solutions trap), confirm the credit.">
</p>

[**`refund-request-process.md`**](./refund-request-process.md) — how to get a refund or credit for an Azure billing charge, including:

- where the invoice actually lives;
- the self-service refund tool's **hidden "expedited refund" limit**;
- filing a support ticket as a **Credit request** instead, and the **"Solutions" self-help trap** that sends you in a circle (plus a broken link in the wizard);
- how to confirm it worked, and known flakiness to expect.

## License

MIT. See [LICENSE](LICENSE).

<!-- org-footer -->
---

<p align="center"><sub>Part of <a href="https://github.com/ry-ops">ry-ops</a> · building the pipes between infrastructure, automation, and observability · built by <a href="https://github.com/ry-ops">ry-ops</a></sub></p>
