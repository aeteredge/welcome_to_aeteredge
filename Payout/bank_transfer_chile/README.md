# 📄 Payload for `payout-invoice` (Bank Transfer - Chile - CLP)

This document outlines the structure and required fields for the `payout-invoice` payload using the `bank_transfer_clp` service, which supports **bank transfers in Chile (CLP)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                         |
| -------------- | ------------------------------------------------------------------- |
| `reference_id` | Unique identifier for the payout request (used for tracking).       |
| `service`      | Must be `"bank_transfer_clp"` for CLP bank transfer payouts.        |
| `currency`     | Must be `"CLP"` for Chilean Peso.                                   |
| `amount`       | Amount to be paid out (integer, no decimal places).                 |
| `test_mode`    | Set to `true` for test/sandbox mode, `false` for live transactions. |

---

### 🏦 Fields (nested under `fields`)

| JSON Key                    | Description                                                   |
| --------------------------- | ------------------------------------------------------------- |
| `bank_code`                 | Bank name or bank code.                                       |
| `account_type`              | Type of account. Accepted values: `CC`, `SVGS`.               |
| `bank_account`              | Bank account number of the beneficiary.                       |
| `beneficiary_document_type` | Type of document. Accepted values: `RUT`, `RUN`, `PAS`, `CE`. |
| `beneficiary_document_id`   | Document number, Tax ID, or document code of the beneficiary. |
| `beneficiary_name`          | Full name of the beneficiary.                                 |
| `sender_full_name`          | Full name of the payer/sender.                                |

📝 **Important:** These keys must be **nested under `fields`**

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

- All amounts must be provided in **Chilean Pesos (CLP)** as integers.
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
