# 📄 Payload for `payment-invoices` (Peru - PE)

This document outlines the structure and required fields for the `payment-invoices` payload using the `bank_transfer_pen_invoice` service, which supports **pay-ins via bank transfers in Peru (PEN)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key              | Description                                                         |
| --------------------- | ------------------------------------------------------------------- |
| `reference_id`        | Unique identifier for the payment request.                          |
| `service`             | Must be `"bank_transfer_pen_invoice"` for PE bank transfer pay-ins. |
| `currency`            | Must be `"PEN"` for Peruvian Soles.                                 |
| `amount`              | Amount to be paid.                                                  |
| `description`         | Description of the payment purpose.                                 |
| `test_mode`           | Set to `true` for test/sandbox transactions.                        |
| `return_urls.success` | Redirect URL after a successful payment.                            |
| `return_urls.pending` | Redirect URL while payment is pending.                              |
| `return_urls.fail`    | Redirect URL after a failed payment.                                |
| `callback_url`        | URL to receive asynchronous status updates.                         |

---

### 👤 Customer (nested under `customer`)

| JSON Key            | Description                               |
| ------------------- | ----------------------------------------- |
| `reference_id`      | Unique identifier of the customer.        |
| `individual_tax_id` | The customer's tax identification number. |
| `name`              | Full name of the customer.                |
| `email`             | Email address of the customer.            |
| `phone`             | Phone number of the customer.             |
| `date_of_birth`     | Date of birth in the format `YYYY-MM-DD`. |

---

### 🏠 Address (nested under `customer.address`)

| JSON Key       | Description                             |
| -------------- | --------------------------------------- |
| `full_address` | Full formatted address string.          |
| `country`      | Country code (must be `"PE"` for Peru). |
| `region`       | Province or region.                     |
| `city`         | City name.                              |
| `street`       | Street name and number.                 |
| `post_code`    | Postal code.                            |

---

### 🧩 Metadata

| JSON Path              | Description                 |
| ---------------------- | --------------------------- |
| `customer.metadata.ip` | IP address of the customer. |
| `metadata.url`         | URL of the company.         |

---

## 🔍 Notes

- All amounts must be provided in **Peruvian Soles (PEN)** as whole numbers (integer).
- Use `test_mode: true` to simulate transactions in a sandbox environment.
- Callback and redirect URLs must be HTTPS for secure communications.

## 🎯 Approving transactions in sandbox

When using `test_mode: true`, you can simulate different payment outcomes by setting specific values in the `amount` field:

| Test Amount | Behavior                                    |
| ----------- | ------------------------------------------- |
| `99997`     | Triggers a **successful** payment callback. |
| `99999`     | Triggers a **declined** payment callback.   |

---
