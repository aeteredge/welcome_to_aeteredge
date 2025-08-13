# 📄 Payload for `payment-invoice` (SPEI - Mexico - MXN)

This document outlines the structure and required fields for the `payment-invoice` payload using the `spei_mxn_invoice` service, which supports **bank transfers via SPEI in Mexican Pesos (MXN)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key              | Description                                             |
| --------------------- | ------------------------------------------------------- |
| `reference_id`        | Unique identifier for the payment request.              |
| `service`             | Must be `"spei_mxn_invoice"` for SPEI invoice payments. |
| `currency`            | Must be `"MXN"` for Mexican Pesos.                      |
| `amount`              | Amount to be paid, as an integer (in cents).            |
| `description`         | Description of the payment (e.g., location or reason).  |
| `test_mode`           | Set to `true` for test/sandbox transactions.            |
| `return_urls.success` | Redirect URL after a successful payment.                |
| `return_urls.pending` | Redirect URL while payment is pending.                  |
| `return_urls.fail`    | Redirect URL after a failed payment.                    |
| `callback_url`        | URL to receive asynchronous status updates (webhook).   |

---

### 👤 Customer (nested under `customer`)

| JSON Key            | Description                                                          |
| ------------------- | -------------------------------------------------------------------- |
| `reference_id`      | Unique identifier of the customer.                                   |
| `individual_tax_id` | Customer's tax identification number.                                |
| `name`              | Full name of the customer.                                           |
| `email`             | Email address of the customer.                                       |
| `phone`             | Phone number of the customer (must include country code, e.g. `52`). |
| `date_of_birth`     | Customer's date of birth in format `YYYY-MM-DD`.                     |

---

### 🏠 Address (nested under `customer.address`)

| JSON Key       | Description                               |
| -------------- | ----------------------------------------- |
| `full_address` | Full formatted address string.            |
| `country`      | Country code (must be `"MX"` for Mexico). |
| `region`       | State or region.                          |
| `city`         | City name.                                |
| `street`       | Street name and number.                   |
| `post_code`    | Postal code.                              |

---

### 🧩 Metadata

| JSON Path              | Description                 |
| ---------------------- | --------------------------- |
| `customer.metadata.ip` | IP address of the customer. |
| `metadata.url`         | URL of the company.         |

---

## 🔍 Notes

- All amounts must be provided in **Mexican Pesos (MXN)** as whole numbers (in cents).
- Use `test_mode: true` to simulate transactions in a sandbox environment.
- Callback and redirect URLs must use HTTPS for secure communications.
- This service creates a **payment invoice** for a bank transfer via SPEI in Mexico.

## 🎯 Approving transactions in sandbox

When using `test_mode: true`, you can simulate different payment outcomes by setting specific values in the `amount` field:

| Test Amount | Behavior                                    |
| ----------- | ------------------------------------------- |
| `99997`     | Triggers a **successful** payment callback. |
| `99999`     | Triggers a **declined** payment callback.   |

---
