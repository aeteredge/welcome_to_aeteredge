# 📄 Payload for `payment-invoices` (BLIK - Poland - PLN)

This document outlines the structure and required fields for the `payment-invoices` payload using the `blik_pln_hpp` service, which supports **hosted pay-ins using BLIK in Polish Złoty (PLN)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key             | Description                                                                 |
|----------------------|-----------------------------------------------------------------------------|
| `reference_id`       | Unique identifier for the payment request.                                  |
| `description`        | Description of the payment purpose.                                         |
| `currency`           | Must be `"PLN"` for Polish Złoty.                                           |
| `amount`             | Amount to be paid.                                                          |
| `service`            | Must be `"blik_pln_hpp"` for BLIK hosted payments.                          |
| `flow`               | Payment flow. Use `"charge"` for hosted page flow.                          |
| `return_urls.success`| Redirect URL after a successful payment.                                    |
| `return_urls.fail`   | Redirect URL after a failed payment.                                        |
| `return_urls.pending`| Redirect URL while payment is pending.                                      |
| `callback_url`       | URL to receive asynchronous status updates.                                 |
| `test_mode`          | Set to `true` for test/sandbox mode, `false` for live transactions.         |

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
| `country`        | Country code (must be `"PL"` for Poland).                                   |
| `region`         | Province or region.                                                         |
| `city`           | City name.                                                                  |
| `post_code`      | Postal code.                                                                |

---

### 🧩 Metadata

| JSON Path                     | Description                                                                                                    |
|-------------------------------|----------------------------------------------------------------------------------------------------------------|
| `metadata.url`                | URL of the company.                                                                                            |
| `metadata.FTD`                | **First Time Deposit indicator.** It's very important to include this parameter. Set to `"true"` if this is the **customer's first deposit**, or `"false"` if the **traffic is trusted**.                                                                        |
| `customer.metadata.ip`        | IP address of the customer.                                                                                    |

---

## 🔍 Notes

- All amounts must be provided in **Polish Złoty (PLN)** as whole numbers (integer).
- Set `test_mode: true` to use sandbox environment, or `false` for live transactions.
- Callback and redirect URLs must be HTTPS for secure communications.
- This service uses a hosted payment page (HPP) via BLIK.

---
