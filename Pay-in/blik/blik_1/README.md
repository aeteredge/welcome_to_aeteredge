# 📄 Payload for `payment-invoices` (BLIK - Poland - PLN)

This document outlines the structure and required fields for the `payment-invoices` payload using the `blik_pln_hpp` service, which supports **hosted pay-ins using BLIK in Polish Złoty (PLN)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key              | Description                                                         |
| --------------------- | ------------------------------------------------------------------- |
| `reference_id`        | Unique identifier for the payment request.                          |
| `service`             | Must be `"blik_pln_hpp"` for BLIK hosted payments.                  |
| `currency`            | Must be `"PLN"` for Polish Złoty.                                   |
| `amount`              | Amount to be paid.                                                  |
| `description`         | Description of the payment purpose.                                 |
| `test_mode`           | Set to `true` for test/sandbox mode, `false` for live transactions. |
| `flow`                | Payment flow. Use `"charge"` for hosted page flow.                  |
| `return_urls.success` | Redirect URL after a successful payment.                            |
| `return_urls.pending` | Redirect URL while payment is pending.                              |
| `return_urls.fail`    | Redirect URL after a failed payment.                                |
| `callback_url`        | URL to receive asynchronous status updates.                         |

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

| JSON Key       | Description                               |
| -------------- | ----------------------------------------- |
| `full_address` | Full formatted address string.            |
| `country`      | Country code (must be `"PL"` for Poland). |
| `region`       | Province or region.                       |
| `city`         | City name.                                |
| `post_code`    | Postal code.                              |

---
### 🧩 Metadata
| JSON Path              | Description                               |
| ---------------------- | ----------------------------------------- |
| `customer.metadata.ip` | IP address of the customer.               |
| `metadata.url`         | URL of the company or merchant site.      |
| `metadata.FTD`         | **First Time Deposit indicator.** Set to `"true"` if this is the **customer's first deposit**, or `"false"` if the transaction is from a trusted/repeat customer or traffic.            |

---

## 🔍 Notes

- All amounts must be provided in **Polish Złoty (PLN)** as whole numbers (integer).
- Set `test_mode: true` to use sandbox environment, or `false` for live transactions.
- Callback and redirect URLs must be HTTPS for secure communications.
- This service uses a hosted payment page (HPP) via BLIK.

## 🎯 Approving transactions in sandbox

When using `test_mode: true`, you can simulate different payment outcomes by setting specific values in the `amount` field:

| Test Amount        | Behavior                                    |
| ------------------ | ------------------------------------------- |
| `777000 to 777999` | Triggers a **successful** payment callback. |
| `000000 to 77699`  | Triggers a **fail/retry** payment callback. |
| `778000 to 999999` | Triggers a **fail/retry** payment callback. |

---
