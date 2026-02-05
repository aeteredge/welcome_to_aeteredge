# 📄 Payload for `payment-invoices` (Chile – CL)

This document outlines the structure and required fields for the `payment-invoices` payload using the **`wallet_aggregated_clp_hpp`** service, which supports **aggregated wallet pay-ins in Chile (CLP)** through a **Hosted Payment Page (HPP)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing or invalid, the request will be rejected.

---

### 🧾 Root Attributes (nested under `data.attributes`)

| JSON Key              | Description                                         |
| --------------------- | --------------------------------------------------- |
| `reference_id`        | Unique identifier for the payment request.          |
| `service`             | Must be `"wallet_aggregated_clp_hpp"`.              |
| `currency`            | Must be `"CLP"` (Chilean Peso).                     |
| `amount`              | Amount to be paid.                                  |
| `description`         | Description of the payment purpose.                 |
| `test_mode`           | Set to `true` for test/sandbox transactions.        |
| `customer`            | Customer information object.                        |
| `return_urls.success` | Redirect URL after a successful payment.            |
| `return_urls.pending` | Redirect URL while the payment is pending.          |
| `return_urls.fail`    | Redirect URL after a failed payment.                |
| `callback_url`        | URL to receive asynchronous payment status updates. |

---

### 👤 Customer (nested under `customer`)

| JSON Key            | Description                                          |
| ------------------- | ---------------------------------------------------- |
| `reference_id`      | Unique identifier of the customer.                   |
| `individual_tax_id` | Customer identification number (e.g. RUT).           |
| `name`              | Full name of the customer.                           |
| `email`             | Email address of the customer.                       |
| `phone`             | Phone number of the customer (international format). |
| `metadata.ip`       | IP address of the customer.                          |

---

## 🔍 Notes

- All amounts must be provided in **Chilean Pesos (CLP)**.
- The `wallet_aggregated_clp_hpp` service uses a **Hosted Payment Page (HPP)** where the customer selects and completes the payment using one of the available wallets.
- Use `test_mode: true` to simulate transactions in a sandbox environment.
- The `individual_tax_id` must be valid according to Chilean regulations for production transactions.
- All `return_urls` and the `callback_url` must be **HTTPS** endpoints.
