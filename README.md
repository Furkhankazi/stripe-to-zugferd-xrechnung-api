# Stripe Invoice → Germany ZUGFeRD 2.2 / XRechnung 3.0.2 (EN 16931)

Starting **January 1, 2027**, German B2B businesses with >€800k prior-year revenue must issue structured EN 16931 e-invoices (plain Stripe PDFs are no longer valid VAT invoices).

This starter shows how to turn a raw Stripe invoice payload into a KoSIT-validated **ZUGFeRD 2.2 (PDF/A-3b)** or **XRechnung 3.0.2** XML in one REST call using [Invora](https://invora.dev) (hosted in AWS Frankfurt `eu-central-1`, Zero-PII GDPR ledger).

## Free Zero-Login Tools & Docs
- **Live KoSIT XRechnung 3.0.2 / ZUGFeRD Validator:** https://invora.dev/tools/xrechnung-zugferd-validator
- **Leitweg-ID & VAT Checker:** https://invora.dev/tools/leitweg-id-vat-checker
- **ZATCA Phase 2 QR / XML Debugger:** https://invora.dev/tools/zatca-qr-xml-debugger
- **Interactive API Docs (Postman):** https://documenter.getpostman.com/view/60396935/2sBYPv4D6P

## Quick Example (Node.js)
```js
const res = await fetch("[https://api.invora.dev/v1/einvoice/issue](https://api.invora.dev/v1/einvoice/issue)", {
  method: "POST",
  headers: {
    "Authorization": `Bearer ${process.env.INVORA_API_KEY}`,
    "Content-Type": "application/json",
    "Idempotency-Key": "inv_2027_0001"
  },
  body: JSON.stringify({
    profile: "ZUGFERD_2_2",
    stripeInvoice: rawStripeInvoiceObject
  })
});
const data = await res.json();# stripe-to-zugferd-xrechnung-api
Convert Stripe invoices to KoSIT-validated Germany XRechnung 3.0 &amp; ZUGFeRD 2.2 (PDF/A-3b) before Jan 1, 2027.
