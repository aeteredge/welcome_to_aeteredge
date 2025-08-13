# 📄 Payload for `payout-invoice` (Peru - PE)

This document outlines the structure and required fields for the `payout-invoice` payload using the `bank_transfer_pen` service, which supports **bank transfers in Peru (PEN)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be nested inside the `fields` object of the payload.  
If any of them is missing or placed outside of `fields`, the request will be rejected.

| JSON Key                  | Description                                                   |
| ------------------------- | ------------------------------------------------------------- |
| `bank_code`               | Bank name or bank code.                                       |
| `account_type`            | Type of account. Accepted values: `CC`, `SVGS`.               |
| `account_number`          | Beneficiary's bank account number.                            |
| `document_type`           | Type of document. Accepted values: `RUC`, `DNI`, `PAS`, `CE`. |
| `beneficiary_document_id` | Document number, Tax ID, or document code of the beneficiary. |
| `beneficiary_name`        | Full name of the beneficiary.                                 |
| `beneficiary_city`        | City or region where the account is held.                     |
| `bank_account`            | CCI number (Interbank account code).                          |
| `sender_full_name`        | Full name of the payer/sender.                                |

📝 **Important:** These keys must be **nested under `fields`**

---

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                         |
| -------------- | ------------------------------------------------------------------- |
| `reference_id` | Unique identifier for the payout request (used for tracking).       |
| `service`      | Must be `"bank_transfer_pen"` for PEN bank transfer payouts.        |
| `currency`     | Must be `"PEN"` for Peruvian Sol.                                   |
| `amount`       | Amount to be paid out (integer, no decimal places).                 |
| `test_mode`    | Set to `true` for test/sandbox mode, `false` for live transactions. |

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

- All amounts must be provided in **Peruvian Sol (PEN)** as integers.
- `reference_id` must be unique for each payout.
- `test_mode: true` indicates the payout will be processed in sandbox mode.
- The `bank_account` (CCI) is different from the `account_number` — ensure both are provided correctly.

---

## 🎯 Approving Transactions in Sandbox

When using `test_mode: true`, you can simulate different payout outcomes by setting specific values in the `amount` field:

| Test Amount | Behavior                                   |
| ----------- | ------------------------------------------ |
| `99997`     | Triggers a **successful** payout callback. |
| `99999`     | Triggers a **declined** payout callback.   |

---
