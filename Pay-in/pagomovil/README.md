# 📄 Payload for `payment-invoices` (PagoMóvil - Venezuela - VES)

This document outlines the structure and required fields for the `payment-invoices` payload using the `pagomovil_ves_invoice` service, which supports **PagoMóvil payments in Venezuela (VES)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                         |
| -------------- | ------------------------------------------------------------------- |
| `reference_id` | Unique identifier for the payment request.                          |
| `service`      | Must be `"pagomovil_ves_invoice"` for PagoMóvil in Venezuela.       |
| `currency`     | Must be `"VES"` for Venezuelan Bolívar.                             |
| `amount`       | Amount to be paid.                                                  |
| `description`  | Description of the payment purpose.                                 |
| `test_mode`    | Set to `true` for test/sandbox mode, `false` for live transactions. |
| `success`      | Redirect URL after a successful payment.                            |
| `pending`      | Redirect URL while the payment is pending.                          |
| `fail`         | Redirect URL after a failed payment.                                |
| `callback_url` | URL to receive asynchronous status updates.                         |

---

### 🧩 Metadata

| JSON Path                | Description                 |
| ------------------------ | --------------------------- |
| `attributes.metadata.ip` | IP address of the customer. |
| `metadata.url`           | URL of the company.         |

---

## 🔍 Notes

- All amounts must be provided in **Venezuelan Bolívar (VES)** as integers.
- `reference_id` must be unique for each transaction.
- Use `test_mode: true` to simulate transactions in the sandbox environment.
- Callback and redirect URLs must be HTTPS for secure communications.
- Integration supports **PagoMóvil invoice-based payments**.

---
