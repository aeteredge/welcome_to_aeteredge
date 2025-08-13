# 📄 Payload for `payment-invoices` (UPI - India - INR)

This document outlines the structure and required fields for the `payment-invoices` payload using the `upi_inr_hpp` service, which supports **hosted pay-ins using UPI in Indian Rupees (INR)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key              | Description                                                          |
| --------------------- | -------------------------------------------------------------------- |
| `reference_id`        | Unique identifier for the payment request.                           |
| `service`             | Must be `"upi_inr_hpp"` for UPI hosted payments.                     |
| `currency`            | Must be `"INR"` for Indian Rupees.                                   |
| `amount`              | Amount to be paid.                                                   |
| `test_mode`           | Set to `true` for sandbox testing, or `false` for live transactions. |
| `return_urls.success` | Redirect URL after a successful payment.                             |
| `return_urls.pending` | Redirect URL while payment is pending.                               |
| `return_urls.fail`    | Redirect URL after a failed payment.                                 |
| `callback_url`        | URL to receive asynchronous status updates.                          |

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

| JSON Key       | Description                              |
| -------------- | ---------------------------------------- |
| `country`      | Country code (must be `"IN"` for India). |
| `city`         | City name.                               |
| `full_address` | Full formatted address string.           |
| `post_code`    | Postal code.                             |
| `region`       | Province or region.                      |
| `street`       | Street name and number.                  |

---

### 🧩 Metadata

| JSON Path                        | Description                   |
| -------------------------------- | ----------------------------- |
| `customer.metadata.ip`           | IP address of the customer.   |
| `customer.metadata.client_agent` | Browser or user-agent string. |
| `metadata.url`                   | URL of the company.           |

---

## 🔍 Notes

- All amounts must be provided in **Indian Rupees (INR)** as whole numbers (integer).
- Use `test_mode: true` to simulate transactions in a sandbox environment.
- Callback and redirect URLs must be HTTPS for secure communications.
- This service uses a hosted payment page (HPP) for UPI-based transactions.

---
