# 📄 Payload for `payment-invoice` (Efecty - Colombia - COP)

This document outlines the structure and required fields for the `payment-invoice` payload using the `efecty_cop_hpp` service, which supports **hosted pay-ins using Efecty in Colombian Pesos (COP)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key              | Description                                            |
| --------------------- | ------------------------------------------------------ |
| `reference_id`        | Unique identifier for the payment request.             |
| `service`             | Must be `"efecty_cop_hpp"` for Efecty hosted payments. |
| `currency`            | Must be `"COP"` for Colombian Pesos.                   |
| `amount`              | Amount to be paid.                                     |
| `test_mode`           | Set to `true` for test/sandbox transactions.           |
| `flow`                | Payment flow. Use `"charge"` for hosted page flow.     |
| `return_urls.success` | Redirect URL after a successful payment.               |
| `return_urls.pending` | Redirect URL while payment is pending.                 |
| `return_urls.fail`    | Redirect URL after a failed payment.                   |
| `callback_url`        | URL to receive asynchronous status updates.            |

---

### 👤 Customer (nested under `customer`)

| JSON Key            | Description                           |
| ------------------- | ------------------------------------- |
| `reference_id`      | Unique identifier of the customer.    |
| `individual_tax_id` | Customer's tax identification number. |
| `name`              | Full name of the customer.            |
| `email`             | Email address of the customer.        |
| `phone`             | Phone number of the customer.         |

---

### 🏠 Address (nested under `customer.address`)

| JSON Key       | Description                                 |
| -------------- | ------------------------------------------- |
| `full_address` | Full formatted address string.              |
| `country`      | Country code (must be `"CO"` for Colombia). |
| `region`       | Province or region.                         |
| `city`         | City name.                                  |
| `street`       | Street name and number.                     |
| `post_code`    | Postal code.                                |

---

### 🧩 Metadata

| JSON Path              | Description                 |
| ---------------------- | --------------------------- |
| `metadata.url`         | URL of the company.         |
| `customer.metadata.ip` | IP address of the customer. |

---

## 🔍 Notes

- All amounts must be provided in **Colombian Pesos (COP)** as whole numbers (integer).
- Use `test_mode: true` to simulate transactions in a sandbox environment.
- Callback and redirect URLs must be HTTPS for secure communications.
- This service uses a hosted payment page (HPP) for Efecty transactions.

---
