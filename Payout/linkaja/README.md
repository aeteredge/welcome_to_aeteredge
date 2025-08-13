# 📄 Payload for `payout-invoice` (Indonesia - ID)

This document outlines the structure and required fields for the `payout-invoice` payload using the `linkaja_idr` service, which supports **LinkAja wallet transfers in Indonesia (ID)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be nested inside the `fields` object of the payload.  
If any of them is missing or placed outside of `fields`, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                    |
| -------------- | -------------------------------------------------------------- |
| `reference_id` | Unique identifier for the payout request (used for tracking).  |
| `service`      | Must be `"linkaja_idr"` for LinkAja wallet payouts.            |
| `currency`     | Must be `"IDR"` for Indonesian Rupiah.                         |
| `amount`       | Amount to be paid out (**integer**, no decimal places).        |
| `test_mode`    | Set to `true` for sandbox mode, `false` for live transactions. |

---

### 📂 Fields (nested under `fields`)

| JSON Key              | Description                           |
| --------------------- | ------------------------------------- |
| `bank_account_name`   | Name of the LinkAja account holder.   |
| `bank_account_number` | LinkAja account number or identifier. |

📝 **Important:** These keys must be **nested under `fields`**

---

### 👤 Customer (nested under `customer`)

| JSON Key       | Description                                 |
| -------------- | ------------------------------------------- |
| `reference_id` | Unique identifier for the recipient.        |
| `name`         | Full name of the recipient.                 |
| `email`        | Email address of the recipient.             |
| `phone`        | Phone number linked to the LinkAja account. |

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

- All amounts must be provided in **Indonesian Rupiah (IDR)** as integers.
- `reference_id` must be unique for each payout request.
- `test_mode: true` indicates the transaction will be processed in sandbox mode.
- When `auto_process` is set to `false`, manual approval is required in the dashboard.
- Make sure the `customer` object includes all required details for identity verification and compliance.

---
