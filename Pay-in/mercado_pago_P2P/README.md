# 📄 Payload for `payment-invoice` (Argentina – AR)

This document outlines the structure and required fields for the `payment-invoices` payload using the **`bank_transfer_ars_hpp`** service, which supports **pay-ins via bank transfers in Argentina (ARS)** through a **Hosted Payment Page (HPP)**.

---

## ✅ Required Fields

All fields listed below are mandatory and must be correctly nested in their respective objects.  
If any of them is missing, the request will be rejected.

---

## 🧾 Attributes (`data.attributes`)

| JSON Key              | Description                                         |
| --------------------- | --------------------------------------------------- |
| `reference_id`        | Unique identifier for the payment request.          |
| `service`             | Must be `"bank_transfer_ars_hpp"`.                  |
| `currency`            | Must be `"ARS"` for Argentine Pesos.                |
| `amount`              | Amount to be paid.                                  |
| `test_mode`           | Set to `true` for sandbox transactions.             |
| `customer`            | Customer information object.                        |
| `service_fields`      | Service-specific required fields for this route.    |
| `return_urls.success` | Redirect URL after a successful payment.            |
| `return_urls.pending` | Redirect URL while payment is pending.              |
| `return_urls.fail`    | Redirect URL after a failed payment.                |
| `callback_url`        | URL to receive asynchronous payment status updates. |

---

### 👤 Customer (nested under `customer`)

| JSON Key            | Description                                                      |
| ------------------- | ---------------------------------------------------------------- |
| `reference_id`      | Unique identifier of the customer.                               |
| `individual_tax_id` | The customer's tax identification number (e.g., DNI/CUIT/CUIL).  |
| `name`              | Full name of the customer.                                       |
| `email`             | Email address of the customer.                                   |
| `phone`             | Phone number of the customer (international format recommended). |
| `metadata.ip`       | IP address of the customer.                                      |

---

## 🔍 Notes

- All amounts must be provided in **Argentine Pesos (ARS)**.
- Use `test_mode: true` to simulate transactions in a sandbox environment.
- Callback and redirect URLs must be HTTPS for secure communications.
- The customer will be redirected to a **Hosted Payment Page (HPP)** to complete the bank transfer.
