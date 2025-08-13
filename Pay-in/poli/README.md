# 📄 Payload for `payment-invoices` (PoliPay Online - New Zealand Dollar - NZD)

This document outlines the structure and required fields for the `payment-invoices` payload using the `polipayonline_nzd_hpp` service, which supports **hosted pay-ins via PoliPay Online in New Zealand Dollar (NZD)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                                  |
| -------------- | ---------------------------------------------------------------------------- |
| `reference_id` | Unique identifier for the payment request.                                   |
| `service`      | Must be `"polipayonline_nzd_hpp"` for PoliPay Online hosted payments in NZD. |
| `currency`     | Must be `"NZD"` for New Zealand Dollar.                                      |
| `amount`       | Amount to be paid.                                                           |
| `description`  | Description of the payment purpose.                                          |
| `test_mode`    | Set to `false` for live/production transactions.                             |
| `flow`         | Payment flow. Use `"charge"` for hosted page flow.                           |
| `return_url`   | Redirect URL after a payment (success, fail, or pending).                    |
| `callback_url` | URL to receive asynchronous status updates.                                  |

---

### 👤 Customer (nested under `customer`)

| JSON Key       | Description                        |
| -------------- | ---------------------------------- |
| `reference_id` | Unique identifier of the customer. |
| `name`         | Full name of the customer.         |
| `email`        | Email address of the customer.     |
| `phone`        | Phone number of the customer.      |

---

### 🏠 Address (nested under `customer.address`)

| JSON Key    | Description                                    |
| ----------- | ---------------------------------------------- |
| `country`   | Country code (must be `"NZ"` for New Zealand). |
| `city`      | City name.                                     |
| `street`    | Street name and number.                        |
| `post_code` | Postal code.                                   |

---

### 🧩 Metadata

| JSON Path           | Description                          |
| ------------------- | ------------------------------------ |
| `metadata.site_url` | URL of the company or merchant site. |

---

## 🔍 Notes

- All amounts must be provided in **New Zealand Dollar (NZD)** as whole numbers (integer).
- Use `test_mode: false`. Testing can only be performed in the production environment.
- Callback and redirect URLs must be HTTPS for secure communications.
- This service uses a hosted payment page (HPP) via PoliPay Online.

---
