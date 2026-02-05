# 📄 Payload for `payment-invoices` (Argentina – AR)

This document outlines the structure and required fields for the `payment-invoices` payload using the **`bank_transfer_ars_hpp`** service, which supports **pay-ins via bank transfers in Argentina (ARS)** through a **Hosted Payment Page (HPP)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing, the request will be rejected.

---

### 🧾 Root Attributes (nested under `data.attributes`)

| JSON Key              | Description                                                     |
| --------------------- | --------------------------------------------------------------- |
| `reference_id`        | Unique identifier for the payment request.                      |
| `service`             | Must be `"bank_transfer_ars_hpp"` for AR bank transfer pay-ins. |
| `currency`            | Must be `"ARS"` for Argentine Pesos.                            |
| `amount`              | Amount to be paid.                                              |
| `test_mode`           | Set to `true` for test/sandbox transactions.                    |
| `customer`            | Customer information object.                                    |
| `service_fields`      | Service-specific required fields.                               |
| `return_urls.success` | Redirect URL after a successful payment.                        |
| `return_urls.pending` | Redirect URL while the payment is pending.                      |
| `return_urls.fail`    | Redirect URL after a failed payment.                            |
| `callback_url`        | URL to receive asynchronous payment status updates.             |

---

### 👤 Customer (nested under `customer`)

| JSON Key        | Description                               |
| --------------- | ----------------------------------------- |
| `reference_id`  | Unique identifier of the customer.        |
| `name`          | Full name of the customer.                |
| `email`         | Email address of the customer.            |
| `phone`         | Phone number of the customer.             |
| `date_of_birth` | Date of birth in the format `YYYY-MM-DD`. |
| `address`       | Customer address information.             |

---

### 🏠 Address (nested under `customer.address`)

| JSON Key       | Description                                  |
| -------------- | -------------------------------------------- |
| `full_address` | Full formatted address string.               |
| `country`      | Country code (must be `"AR"` for Argentina). |
| `region`       | Province or region.                          |
| `city`         | City name.                                   |
| `street`       | Street name and number.                      |
| `post_code`    | Postal code.                                 |

---

### 🧩 Service Fields

| JSON Key      | Description                                  |
| ------------- | -------------------------------------------- |
| `document_id` | Customer identification document (e.g. DNI). |

---

## 🔍 Notes

- All amounts must be provided in **Argentine Pesos (ARS)**.
- The `bank_transfer_ars_hpp` service uses a **Hosted Payment Page (HPP)** where the customer is redirected to complete the payment.
- Use `test_mode: true` to simulate transactions in a sandbox environment.
- The `document_id` field is mandatory for customer validation in Argentina.
- All `return_urls` and the `callback_url` must be **HTTPS** endpoints.
