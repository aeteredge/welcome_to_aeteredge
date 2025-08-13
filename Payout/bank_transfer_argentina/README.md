# 📄 Payload for `payout-invoice` (Bank Transfer - Argentina - ARS)

This document outlines the structure and required fields for the `payout-invoice` payload using the `bank_transfer_ars` service, which supports **bank transfers in Argentina (ARS)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                         |
| -------------- | ------------------------------------------------------------------- |
| `reference_id` | Unique identifier for the payout request (used for tracking).       |
| `service`      | Must be `"bank_transfer_ars"` for ARS bank transfer payouts.        |
| `currency`     | Must be `"ARS"` for Argentine Peso.                                 |
| `amount`       | Amount to be paid out (integer, no decimal places).                 |
| `test_mode`    | Set to `true` for test/sandbox mode, `false` for live transactions. |

---

### 🏦 Fields (nested under `fields`)

| JSON Key         | Description                                       |
| ---------------- | ------------------------------------------------- |
| `account_type`   | Type of account. Accepted values: `CBU`, `ALIAS`. |
| `account_number` | CBU or ALIAS of the beneficiary.                  |

📝 **Important:** These keys must be **nested under `fields`**.

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

- All amounts must be provided in **Argentine Pesos (ARS)** as integers.
- `reference_id` must be unique for each payout.
- `test_mode: true` indicates the payout will be processed in sandbox mode.

---

## 🎯 Approving Transactions in Sandbox

When using `test_mode: true`, you can simulate different payout outcomes by setting specific values in the `amount` field:

| Test Amount | Behavior                                   |
| ----------- | ------------------------------------------ |
| `99997`     | Triggers a **successful** payout callback. |
| `99999`     | Triggers a **declined** payout callback.   |

---
