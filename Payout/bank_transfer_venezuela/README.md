# 📄 Payload for `payout-invoice` (Bank Transfer - Venezuela - VES)

This document outlines the structure and required fields for the `payout-invoice` payload using the `bank_transfer_ves` service, which supports **bank transfers in Venezuela (VES)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                         |
| -------------- | ------------------------------------------------------------------- |
| `reference_id` | Unique identifier for the payout request (used for tracking).       |
| `service`      | Must be `"bank_transfer_ves"` for Venezuelan bank transfers.        |
| `currency`     | Must be `"VES"` for Venezuelan Bolívar.                             |
| `amount`       | Amount to be paid out.                                              |
| `description`  | Optional description for the payout.                                |
| `test_mode`    | Set to `true` for test/sandbox mode, `false` for live transactions. |
| `callback_url` | URL to receive asynchronous status updates.                         |

---

### 🏦 Fields (nested under `fields`)

| JSON Key                    | Description                                                            |
| --------------------------- | ---------------------------------------------------------------------- |
| `bank_code`                 | Bank code of the beneficiary’s bank (e.g., `0134`).                    |
| `bank_account`              | Bank account number of the beneficiary.                                |
| `beneficiary_document_type` | Document type of the beneficiary. Accepted values: `CI`, `RIF`, `PAS`. |
| `beneficiary_document_id`   | Document number or tax ID of the beneficiary.                          |
| `beneficiary_name`          | Full name of the beneficiary.                                          |

📝 **Important:** These keys must be **nested under `fields`**.

---

### ⚙️ Options (nested under `options`)

| JSON Key       | Description                                                                                           |
| -------------- | ----------------------------------------------------------------------------------------------------- |
| `auto_process` | Set to `true` to automatically process the payout, or `false` for manual approval from the dashboard. |

---

## 🔍 Notes

- All amounts must be provided in **Venezuelan Bolívar (VES)** as integers (no decimal places).
- `reference_id` must be unique for each payout.
- `test_mode: true` simulates transactions in sandbox mode.
- The `callback_url` must use HTTPS for secure communication.
- This integration supports **bank transfer payouts in Venezuela**.

---
