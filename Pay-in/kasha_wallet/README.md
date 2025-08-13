# 📄 Payload for `payment-invoices` (Kasha Wallet - HPP)

This document outlines the structure and required fields for the `payment-invoices` payload using the `kasha_wallet_{currency}_hpp` service, which supports **hosted pay-ins using Kasha Wallet**.  
The service name is dynamic based on the currency. For example:

- For Chilean Pesos (CLP): `kasha_wallet_clp_hpp`
- For Euros (EUR): `kasha_wallet_eur_hpp`

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key              | Description                                               |
| --------------------- | --------------------------------------------------------- |
| `reference_id`        | Unique identifier for the payment request.                |
| `service`             | Dynamic based on currency: `kasha_wallet_{currency}_hpp`. |
| `currency`            | Currency of the transaction. Affects the service name.    |
| `amount`              | Amount to be paid, as an integer (no decimal places).     |
| `test_mode`           | Set to `true` for sandbox, or `false` for live mode.      |
| `flow`                | Payment flow. Use `"charge"` for hosted page flow.        |
| `return_urls.success` | Redirect URL after a successful payment.                  |
| `return_urls.pending` | Redirect URL while payment is pending.                    |
| `return_urls.fail`    | Redirect URL after a failed payment.                      |
| `callback_url`        | URL to receive asynchronous status updates.               |

---

### 👤 Customer (nested under `customer`)

| JSON Key            | Description                                         |
| ------------------- | --------------------------------------------------- |
| `reference_id`      | Unique identifier of the customer.                  |
| `individual_tax_id` | Optional tax identification number of the customer. |
| `name`              | Full name of the customer.                          |
| `email`             | Email address of the customer.                      |
| `phone`             | Phone number of the customer.                       |

---

### 🏠 Address (nested under `customer.address`)

| JSON Key       | Description                            |
| -------------- | -------------------------------------- |
| `full_address` | Full formatted address string.         |
| `country`      | Country code (e.g., `"CL"` for Chile). |
| `region`       | Province or region.                    |
| `city`         | City name.                             |
| `street`       | Street name and number.                |
| `post_code`    | Postal code.                           |

---

### 🧩 Metadata

| JSON Path                        | Description                                                         |
| -------------------------------- | ------------------------------------------------------------------- |
| `customer.metadata.client_agent` | Required. Browser or user-agent string.                             |
| `customer.metadata.user_device`  | Required. Device type used by the user (e.g., `DESKTOP`, `MOBILE`). |
| `metadata.url`                   | Required. URL of the company.                                       |
| `customer.metadata.ip`           | Required. IP address of the customer.                               |

---

## 🔍 Notes

- The service name must follow the format: `kasha_wallet_{currency}_hpp`.
- All amounts must be provided in the selected currency as whole numbers (integer).
- Use `test_mode: true` for sandbox testing.
- Callback and redirect URLs must use HTTPS for secure communications.

---
