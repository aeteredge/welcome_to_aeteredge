# 📄 Payload for `payout-invoice` (Indonesia - ID)

This document outlines the structure and required fields for the `payout-invoice` payload using the `shopeepay_idr` service, which supports **ShopeePay transfers in Indonesia (ID)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be nested inside the `fields` object of the payload.  
If any of them is missing or placed outside of `fields`, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                    |
| -------------- | -------------------------------------------------------------- |
| `reference_id` | Unique identifier for the payout request (used for tracking).  |
| `service`      | Must be `"shopeepay_idr"` for ShopeePay payouts in Indonesia.  |
| `currency`     | Must be `"IDR"` for Indonesian Rupiah.                         |
| `amount`       | Amount to be paid out (integer, no decimal places).            |
| `test_mode`    | Set to `true` for sandbox mode, `false` for live transactions. |

---

### 🏦 Fields (nested under `fields`)

| JSON Key              | Description                             |
| --------------------- | --------------------------------------- |
| `bank_account_name`   | Name of the ShopeePay account holder.   |
| `bank_account_number` | ShopeePay account number or identifier. |

📝 **Important:** These keys must be **nested under `fields`**

---

### 👤 Customer (nested under `customer`)

| JSON Key       | Description                 |
| -------------- | --------------------------- |
| `reference_id` | Unique customer identifier. |
| `name`         | Full name of the customer.  |
| `email`        | Customer’s email address.   |
| `phone`        | Customer’s phone number.    |

---

### 🧩 Metadata

| JSON Path      | Description                          |
| -------------- | ------------------------------------ |
| `metadata.url` | URL of the company or merchant site. |

---

### ⚙️ Options (nested under `options`)

| JSON Key       | Description                                                                                           |
| -------------- | ----------------------------------------------------------------------------------------------------- |
| `auto_process` | Set to `true` to automatically process the payout, or `false` for manual approval from the dashboard. |

---

## 🔍 Notes

- All amounts must be provided in **Indonesian Rupiah (IDR)** as integers.
- `reference_id` must be unique for each payout.
- `test_mode: true` indicates the payout will be processed in sandbox mode.
- Customer information and metadata must be included as specified above.

---
