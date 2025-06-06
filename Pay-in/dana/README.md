# 📄 Payload for `payment-invoice` (DANA - Indonesia - IDR)

This document outlines the structure and required fields for the `payment-invoice` payload using the `dana_idr_hpp` service, which supports **hosted pay-ins using the DANA wallet in Indonesian Rupiah (IDR)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key             | Description                                                                 |
|----------------------|-----------------------------------------------------------------------------|
| `reference_id`       | Unique identifier for the payment request.                                  |
| `currency`           | Must be `"IDR"` for Indonesian Rupiah.                                      |
| `amount`             | Amount to be paid.                                                          |
| `service`            | Must be `"dana_idr_hpp"` for DANA hosted payments.                          |
| `flow`               | Payment flow. Use `"charge"` for hosted page flow.                          |
| `return_urls.success`| Redirect URL after a successful payment.                                    |
| `return_urls.fail`   | Redirect URL after a failed payment.                                        |
| `return_urls.pending`| Redirect URL while payment is pending.                                      |
| `callback_url`       | URL to receive asynchronous status updates.                                 |
| `test_mode`          | Set to `true` for test/sandbox transactions.                                |

---

### 👤 Customer (nested under `customer`)

| JSON Key             | Description                                                             |
|----------------------|-------------------------------------------------------------------------|
| `reference_id`       | Unique identifier of the customer.                                      |
| `name`               | Full name of the customer.                                              |
| `email`              | Email address of the customer.                                          |
| `phone`              | Phone number of the customer.                                           |
| `individual_tax_id`  | Customer's tax identification number.                                   |

---

### 🏠 Address (nested under `customer.address`)

| JSON Key         | Description                                                                 |
|------------------|-----------------------------------------------------------------------------|
| `full_address`   | Full formatted address string.                                              |
| `country`        | Country code (must be `"ID"` for Indonesia).                                |
| `region`         | Province or region.                                                         |
| `city`           | City name.                                                                  |
| `street`         | Street name and number.                                                     |
| `post_code`      | Postal code.                                                                |

---

### 🧩 Metadata

| JSON Path                        | Description                                                   |
|----------------------------------|---------------------------------------------------------------|
| `metadata.url`                   | URL of the company.                                           |
| `metadata.userDevice`            | Device type used by the user (e.g., `DESKTOP`, `MOBILE`).     |
| `customer.metadata.ip`           | IP address of the customer.                                   |
| `customer.metadata.client_agent` | Browser or user-agent string.                                 |

---

## 🔍 Notes

- All amounts must be provided in **Indonesian Rupiah (IDR)** as whole numbers (integer).
- Use `test_mode: true` to simulate transactions in a sandbox environment.
- Callback and redirect URLs must be HTTPS for secure communications.
- This service uses a hosted payment page (HPP) for DANA wallet transactions.

---
