# 📄 Payload for `payout-invoice` (Colombia - CO)

This document outlines the structure and required fields for the `payout-invoice` payload using the `nequi_cop` service, which supports **Nequi wallet transfers in Colombia (CO)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be nested inside the `fields` object of the payload.  
If any of them is missing or placed outside of `fields`, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                    |
| -------------- | -------------------------------------------------------------- |
| `reference_id` | Unique identifier for the payout request (used for tracking).  |
| `service`      | Must be `"nequi_cop"` for Nequi payouts in Colombia.           |
| `currency`     | Must be `"COP"` for Colombian Pesos.                           |
| `amount`       | Amount to be paid out (**integer**, no decimal places).        |
| `test_mode`    | Set to `true` for sandbox mode, `false` for live transactions. |

---

### 📂 Fields (nested under `fields`)

| JSON Key              | Description                                                       |
| --------------------- | ----------------------------------------------------------------- |
| `bank_account_name`   | Name of the Nequi account holder.                                 |
| `bank_account_number` | Nequi account number or phone number associated with the wallet.  |
| `identity_id`         | National ID or identity number of the beneficiary.                |
| `id_type`             | Type of document. Accepted values: `CC`, `CE`, `PA`, `TI`, `NIT`. |
| `account_type`        | Must be `"0"` for current account and `"1"` for savings account.  |

📝 **Important:** These keys must be **nested under `fields`**

---

### 👤 Customer (nested under `customer`)

| JSON Key       | Description                                 |
| -------------- | ------------------------------------------- |
| `reference_id` | Unique identifier for the recipient.        |
| `name`         | Full name of the recipient.                 |
| `email`        | Email address of the recipient.             |
| `phone`        | Phone number associated with the recipient. |

---

### 🧩 Metadata

| JSON Path      | Description                          |
| -------------- | ------------------------------------ |
| `metadata.url` | URL of the company or merchant site. |

---

### ⚙️ Options (nested under `options`)

| JSON Key       | Description                                                                        |
| -------------- | ---------------------------------------------------------------------------------- |
| `auto_process` | Set to `true` to automatically process the payout, or `false` for manual approval. |

---

## 🔍 Notes

- All amounts must be provided in **Colombian Pesos (COP)** as integers.
- `reference_id` must be unique for each payout request.
- `test_mode: true` indicates the transaction will be processed in sandbox mode.
- When `auto_process` is set to `false`, manual approval is required in the dashboard.
- Ensure the `customer` object contains accurate identity details for compliance.

---
