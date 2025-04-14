# 📄 Payload for `payment-invoices` (Open Banking)

This document outlines the structure and required fields for the `payment-invoices` payload using the `openbanking_eur_hpp` service, which supports **hosted pay-ins via Open Banking in Euros (EUR)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key             | Description                                                                 |
|----------------------|-----------------------------------------------------------------------------|
| `reference_id`       | Unique identifier for the payment request.                                  |
| `description`        | Description of the payment purpose.                                         |
| `currency`           | Must be `"EUR"` for Euro.                                                   |
| `amount`             | Amount to be paid.                                                          |
| `service`            | Must be `"openbanking_eur_hpp"` for Open Banking hosted payments.           |
| `return_url`         | Legacy return URL after completion.                                         |
| `callback_url`       | URL to receive asynchronous status updates.                                 |
| `return_urls.success`| Redirect URL after a successful payment.                                    |
| `return_urls.fail`   | Redirect URL after a failed payment.                                        |
| `return_urls.pending`| Redirect URL while payment is pending.                                      |
| `test_mode`          | Set to `true` for sandbox testing, or `false` for live environment.         |

---

### 👤 Customer (nested under `customer`)

| JSON Key             | Description                                                             |
|----------------------|-------------------------------------------------------------------------|
| `reference_id`       | Unique identifier of the customer.                                      |
| `description`        | Description of the transaction from the customer’s perspective.         |
| `name`               | Full name of the customer.                                              |
| `email`              | Email address of the customer.                                          |
| `phone`              | Phone number of the customer.                                           |
| `date_of_birth`      | Date of birth in the format `YYYY-MM-DD`.                               |

---

### 🏠 Address (nested under `customer.address`)

| JSON Key         | Description                                                                 |
|------------------|-----------------------------------------------------------------------------|
| `country`        | Country code (e.g., `"NL"` for Netherlands).                                |
| `post_code`      | Postal code.                                                                |
| `region`         | Province or region.                                                         |
| `city`           | City name.                                                                  |
| `street`         | Street name and number.                                                     |
| `full_address`   | Full formatted address string.                                              |

---

### 🧩 Metadata

| JSON Path                     | Description                                                   |
|-------------------------------|---------------------------------------------------------------|
| `metadata.url`                | URL of the company.                                           |
| `customer.metadata.ip`        | IP address of the customer.                                   |

---

## 🔍 Notes

- All amounts must be provided in **Euros (EUR)** as whole numbers (integer).
- `test_mode: false` is used for live transactions. Use `true` for sandbox testing.
- Callback and redirect URLs must be HTTPS for secure communications.
- This service uses a hosted payment page (HPP) for Open Banking transactions.

---
