# 📄 Payload for `payment-invoices` (Skrill - Euro - EUR)

This document outlines the structure and required fields for the `payment-invoices` payload using the `skrill_eur_hpp` service, which supports **hosted pay-ins via Skrill in Euro (EUR)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                   |
| -------------- | ------------------------------------------------------------- |
| `reference_id` | Unique identifier for the payment request.                    |
| `service`      | Must be `"skrill_eur_hpp"` for Skrill hosted payments in EUR. |
| `currency`     | Must be `"EUR"` for Euro.                                     |
| `amount`       | Amount to be paid.                                            |
| `description`  | Description of the payment purpose.                           |
| `test_mode`    | Set to `false` for live/production transactions.              |
| `flow`         | Payment flow. Use `"charge"` for hosted page flow.            |
| `return_url`   | Redirect URL after a payment (success, fail, or pending).     |
| `callback_url` | URL to receive asynchronous status updates.                   |

---

### 👤 Customer (nested under `customer`)

| JSON Key       | Description                        |
| -------------- | ---------------------------------- |
| `reference_id` | Unique identifier of the customer. |
| `email`        | Email address of the customer.     |

---

### 🧩 Metadata

| JSON Path           | Description                          |
| ------------------- | ------------------------------------ |
| `metadata.site_url` | URL of the company or merchant site. |

---

## 🔍 Notes

- All amounts must be provided in **Euro (EUR)** as whole numbers (integer).
- Use `test_mode: false`. Testing can only be performed in the production environment.
- Callback and redirect URLs must be HTTPS for secure communications.
- This service uses a hosted payment page (HPP) via Skrill.

---
