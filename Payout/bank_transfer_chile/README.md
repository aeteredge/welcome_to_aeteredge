# 📄 Payload for `payout-invoice` (Chile - CL)

This document outlines the structure and required fields for the `payout-invoice` payload using the `bank_transfer_clp` service, which supports **bank transfers in Chile (CL)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be nested inside the `fields` object of the payload.  
If any of them is missing or placed outside of `fields`, the request will be rejected.

| JSON Key                    | Description                                                                 |
|-----------------------------|-----------------------------------------------------------------------------|
| `bank_code`                 | Bank name or bank code.                                                     |
| `account_type`              | Type of account. Accepted values: `CC`, `SVGS`.                             |
| `bank_account`              | Bank account number of the beneficiary.                                     |
| `beneficiary_document_type` | Type of document. Accepted values: `RUT`, `RUN`, `PAS`, `CE`.               |
| `beneficiary_document_id`   | Document number, Tax ID, or document code of the beneficiary.               |
| `beneficiary_name`          | Full name of the beneficiary.                                               |
| `sender_full_name`          | Full name of the payer/sender.                                              |

📝 **Important:** These keys must be **nested under `fields`**

---

## 🔍 Notes

- `amount` must be provided in **Chilean Pesos (CLP)** as an integer (no decimal places).
- `reference_id` is a unique identifier for the transaction (used for tracking).
- `test_mode: true` indicates this is a simulated transaction.
- Set `auto_process` to `true` or `false` to control whether the transaction is processed automatically. If set to `false`, you will need to approve it manually from the dashboard.
- Additional metadata (e.g., `url`) must be included in the `metadata` object.

---
