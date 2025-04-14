# 📄 Payload for `payment-invoices` (Card Payment)

This document outlines the structure and required fields for the `payment-invoices` payload using the `payment_card_eur_hpp` service, which supports **hosted pay-ins via payment cards**.

---

## ✅ Required Fields – Payment Invoice (HPP)

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key             | Description                                                                               |
|----------------------|-------------------------------------------------------------------------------------------|
| `reference_id`       | Unique identifier for the payment request.                                                |
| `description`        | Description of the payment purpose.                                                       |
| `currency`           | Must be `"EUR"` for Euro and `"USD"` for US Dollar.                                       |
| `amount`             | Amount to be paid.                                                                        |
| `service`            | The service identifier, for example `"payment_card_eur_hpp"` or `"payment_card_usd_hpp"`  |
| `flow`               | Payment flow. Use `"charge"` for hosted page flow.                                        |
| `return_urls.success`| Redirect URL after a successful payment.                                                  |
| `return_urls.fail`   | Redirect URL after a failed payment.                                                      |
| `return_urls.pending`| Redirect URL while payment is pending.                                                    |
| `callback_url`       | URL to receive asynchronous status updates.                                               |
| `test_mode`          | Set to `true` for test/sandbox transactions.                                              |

---

### 👤 Customer (nested under `customer`)

| JSON Key             | Description                                                             |
|----------------------|-------------------------------------------------------------------------|
| `reference_id`       | Unique identifier of the customer.                                      |
| `name`               | Full name of the customer.                                              |
| `email`              | Email address of the customer.                                          |
| `phone`              | Phone number of the customer.                                           |
| `date_of_birth`      | Date of birth in the format `YYYY-MM-DD`.                               |

---

### 🏠 Address (nested under `customer.address`)

| JSON Key         | Description                                                                 |
|------------------|-----------------------------------------------------------------------------|
| `full_address`   | Full formatted address string.                                              |
| `country`        | Country code (e.g., `"ES"` for Spain).                                      |
| `region`         | Province or region.                                                         |
| `city`           | City name.                                                                  |
| `post_code`      | Postal code.                                                                |

---

### 🧩 Metadata

| JSON Path                     | Description                                                   |
|-------------------------------|---------------------------------------------------------------|
| `customer.metadata.ip`        | IP address of the customer.                                   |
| `metadata.url`                | URL of the company.                                           |

---

## 🔍 Notes

- All amounts must be provided in **Euros (EUR) or US Dollar (USD)** as whole numbers (integer).
- Use `test_mode: true` to simulate transactions in a sandbox environment.
- Callback and redirect URLs must be HTTPS for secure communications.
- This integration supports HPP (hosted payment page) for card transactions.

---
