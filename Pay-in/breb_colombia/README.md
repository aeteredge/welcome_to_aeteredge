# 📄 Payload for `payment-invoice` (BREB – Colombia – COP – HPP)

This document outlines the structure and required fields for the `payment-invoice` payload using the `breb_cop_hpp` service, which supports **Hosted Payment Page (HPP) payments in Colombia (COP)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing, the request will be rejected.

---

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key              | Description                                                         |
| --------------------- | ------------------------------------------------------------------- |
| `reference_id`        | Unique identifier for the payment request.                          |
| `service`             | Must be `"breb_cop_hpp"` for BREB Hosted Payment Page transactions. |
| `currency`            | Must be `"COP"` for Colombian Pesos.                                |
| `amount`              | Amount to be paid.                                                  |
| `test_mode`           | Set to `true` for test/sandbox transactions.                        |
| `flow`                | Must be `"charge"` for payment transactions.                        |
| `return_urls.success` | Redirect URL after a successful payment.                            |
| `return_urls.pending` | Redirect URL while payment is pending.                              |
| `return_urls.fail`    | Redirect URL after a failed payment.                                |
| `callback_url`        | URL to receive asynchronous status updates.                         |

---

### 👤 Customer (nested under `customer`)

| JSON Key       | Description                        |
| -------------- | ---------------------------------- |
| `reference_id` | Unique identifier of the customer. |
| `name`         | Full name of the customer.         |
| `email`        | Email address of the customer.     |
| `phone`        | Phone number of the customer.      |
| `metadata.ip`  | IP address of the customer.        |

---

### 🪪 Service Fields (nested under `service_fields`)

| JSON Key        | Description                                      |
| --------------- | ------------------------------------------------ |
| `document_type` | Type of customer document. Accepted value: `CC`. |
| `document_id`   | Customer document number (Cédula de Ciudadanía). |

---

### ⚙️ Gateway Options (nested under `gateway_options.cardgate`)

| JSON Key   | Description                                                             |
| ---------- | ----------------------------------------------------------------------- |
| `tokenize` | Set to `true` to tokenize the card for future usage, otherwise `false`. |

---

## 🔍 Notes

- All amounts must be provided in **Colombian Pesos (COP)**.
- Use `test_mode: true` to simulate transactions in a sandbox environment.
- The payment flow must be `"charge"`.
- Callback and redirect URLs must be HTTPS for secure communications.
