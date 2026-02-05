# 📄 Payload for `payment-invoice` (Argentina – AR)

This document outlines the structure and required fields for the `payment-invoices` payload using the **`bank_transfer_ars_hpp`** service, which supports **pay-ins via bank transfers in Argentina (ARS)** through a **Hosted Payment Page (HPP)**.

---

## ✅ Required Fields

All fields listed below are mandatory and must be correctly nested in their respective objects.  
If any of them is missing, the request will be rejected.

---

## 🧾 Attributes (`data.attributes`)

| JSON Key              | Description                                                |
| --------------------- | ---------------------------------------------------------- |
| `reference_id`        | Unique identifier for the payment request.                 |
| `service`             | Must be `"bank_transfer_ars_hpp"`.                         |
| `currency`            | Must be `"ARS"` for Argentine Pesos.                       |
| `amount`              | Amount to be paid.                                         |
| `test_mode`           | Set to `true` for sandbox transactions.                    |
| `customer`            | Customer information object.                               |
| `service_fields`      | Service-specific required fields for this route.           |
| `return_urls.success` | Redirect URL after a successful payment.                   |
| `return_urls.pending` | Redirect URL while payment is pending.                     |
| `return_urls.fail`    | Redirect URL after a failed payment.                       |
| `callback_url`        | URL to receive asynchronous payment status updates.        |

---

## 👤 Customer (`data.attributes.customer`)

| JSON Key            | Description                                                                |
| ------------------- | -------------------------------------------------------------------------- |
| `reference_id`      | Unique identifier of the customer in your system.                          |
| `individual_tax_id` | Customer tax identification number (e.g., DNI/CUIT/PASS).                  |


---

## 🧩 Service Fields (`data.attributes.service_fields`)

These fields are required for `bank_transfer_ars_hpp` in AR.

| JSON Key         | Description                                                            |
| ---------------- | ---------------------------------------------------------------------- |
| `document_id`    | Customer identification document number (e.g., DNI).                   |
| `document_type`  | Document type (e.g., `dni`). Must match the provider’s allowed values. |
| `account_number` | Customer bank account identifier required by the provider.             |

---

## 🔍 Notes

- All amounts must be provided in **Argentine Pesos (ARS)**.
- Ensure `document_type` matches the **exact enum/value** expected by the provider (case-sensitive in some integrations).
- `return_urls` and `callback_url` should be **HTTPS** for production usage.

---
