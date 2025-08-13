# 📄 Payload for `payment-invoice` (Indonesia - ID)

This document outlines the structure and required fields for the `payment-invoice` payload using the `bank_idr_hpp` service, which supports **pay-ins via virtual accounts (HPP flow) in Indonesia (IDR)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key              | Description                                                 |
| --------------------- | ----------------------------------------------------------- |
| `reference_id`        | Unique identifier for the payment request.                  |
| `service`             | Must be a valid service listed below for supported banks.   |
| `currency`            | Must be `"IDR"` for Indonesian Rupiah.                      |
| `amount`              | Amount to be paid.                                          |
| `test_mode`           | Set to `true` for test/sandbox transactions.                |
| `flow`                | Payment flow. Typically `"charge"` for HPP virtual account. |
| `return_urls.success` | Redirect URL after a successful payment.                    |
| `return_urls.pending` | Redirect URL while payment is pending.                      |
| `return_urls.fail`    | Redirect URL after a failed payment.                        |
| `callback_url`        | URL to receive asynchronous status updates.                 |

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

| JSON Key       | Description                                  |
| -------------- | -------------------------------------------- |
| `full_address` | Full formatted address string.               |
| `country`      | Country code (must be `"ID"` for Indonesia). |
| `region`       | Region or province.                          |
| `city`         | City name.                                   |
| `street`       | Street name and number.                      |
| `post_code`    | Postal code.                                 |

---

### 🧩 Metadata

| JSON Path                        | Description                                               |
| -------------------------------- | --------------------------------------------------------- |
| `customer.metadata.ip`           | IP address of the customer.                               |
| `customer.metadata.client_agent` | Browser or user-agent string.                             |
| `metadata.url`                   | URL of the company.                                       |
| `metadata.userDevice`            | Device type used by the user (e.g., `DESKTOP`, `MOBILE`). |

---

## 🏦 Supported Banks and Their Corresponding Services

To use one of the supported banks, set the corresponding `service` value in the payload:

| Bank Name    | Service Name         |
| ------------ | -------------------- |
| BCA Bank     | `bca_va_idr_hpp`     |
| BNI Bank     | `bni_va_idr_hpp`     |
| BRI Bank     | `bri_va_idr_hpp`     |
| CIMB         | `cimb_ca_idr_hpp`    |
| Mandiri Bank | `mandiri_va_idr_hpp` |
| Permata Bank | `permata_bank_idr`   |

Make sure the correct `service` is selected based on the beneficiary's bank.

---

## 🔍 Notes

- All amounts must be provided in **Indonesian Rupiah (IDR)** as whole numbers (integer).
- Use `test_mode: true` to simulate transactions in a sandbox environment.
- Callback and redirect URLs must be HTTPS for secure communications.

---
