# 📄 Payload for `payment-invoices` (BinancePay - USD)

This document outlines the structure and required fields for the `payment-invoices` payload using the `binancepay_usd_hpp` service, which supports **hosted pay-ins using BinancePay in USD**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key              | Description                                                    |
| --------------------- | -------------------------------------------------------------- |
| `reference_id`        | Unique identifier for the payment request.                     |
| `service`             | Must be `"binancepay_usd_hpp"` for BinancePay hosted payments. |
| `currency`            | Must be `"USD"` for United States Dollar.                      |
| `amount`              | Amount to be paid.                                             |
| `description`         | Description of the payment purpose.                            |
| `test_mode`           | Set to `false` for live/production transactions.               |
| `flow`                | Payment flow. Use `"charge"` for hosted page flow.             |
| `return_urls.success` | Redirect URL after a successful payment.                       |
| `return_urls.pending` | Redirect URL while payment is pending.                         |
| `return_urls.fail`    | Redirect URL after a failed payment.                           |
| `callback_url`        | URL to receive asynchronous status updates.                    |

---

### 👤 Customer (nested under `customer`)

| JSON Key        | Description                               |
| --------------- | ----------------------------------------- |
| `reference_id`  | Unique identifier of the customer.        |
| `name`          | Full name of the customer.                |
| `email`         | Email address of the customer.            |
| `phone`         | Phone number of the customer.             |
| `date_of_birth` | Date of birth in the format `YYYY-MM-DD`. |

---

### 🏠 Address (nested under `customer.address`)

| JSON Key       | Description                            |
| -------------- | -------------------------------------- |
| `full_address` | Full formatted address string.         |
| `country`      | Country code (e.g., `"ES"` for Spain). |
| `region`       | Province or region.                    |
| `street`       | Street name and number.                |
| `city`         | City name.                             |
| `post_code`    | Postal code.                           |

---

### 🧩 Metadata

| JSON Path              | Description                 |
| ---------------------- | --------------------------- |
| `customer.metadata.ip` | IP address of the customer. |
| `metadata.url`         | URL of the company.         |

---

## 🔍 Notes

- All amounts must be provided in **USD** as whole numbers (integer).
- Use `test_mode: false`. Testing can only be performed in the production environment.
- Callback and redirect URLs must be HTTPS for secure communications.

---
