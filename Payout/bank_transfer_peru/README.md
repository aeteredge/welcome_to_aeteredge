# 📄 Payload for `payout-invoice` (Peru - PE)

This document outlines the structure and required fields for the `payout-invoice` payload using the `bank_transfer_pen` service, which supports **bank transfers in Peru (PEN)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be nested inside the `fields` object of the payload.  
If any of them is missing or placed outside of `fields`, the request will be rejected.

| JSON Key                  | Description                                                                 |
|---------------------------|-----------------------------------------------------------------------------|
| `bank_code`               | Bank name or bank code.                                                     |
| `account_type`            | Type of account. Accepted values: `CC`, `SVGS`.                             |
| `account_number`          | Beneficiary's bank account number.                                          |
| `document_type`           | Type of document. Accepted values: `RUC`, `DNI`, `PAS`, `CE`.               |
| `beneficiary_document_id` | Document number, Tax ID, or document code of the beneficiary.               |
| `beneficiary_name`        | Full name of the beneficiary.                                               |
| `beneficiary_city`        | City or region where the account is held.                                   |
| `bank_account`            | CCI number (Interbank account code).                                        |
| `sender_full_name`        | Full name of the payer/sender.                                              |

📝 **Important:** These keys must be **nested under `fields`**

---

## 🔍 Notes

- `amount` must be provided in **Peruvian Soles (PEN)** as an integer (no decimal places).
- `reference_id` is a unique identifier for the transaction (used for tracking).
- `test_mode: true` indicates this is a simulated transaction.
- Set `auto_process` to `true` or `false` to control whether the transaction is processed automatically. If set to `false`, you will need to approve it manually from the dashboard.
- Additional metadata (e.g., `url`) must be included in the `metadata` object.

## 🎯 Approving transactions in sandbox

When using `test_mode: true`, you can simulate different payment outcomes by setting specific values in the `amount` field:

| Test Amount    | Behavior                                    |
|----------------|---------------------------------------------|
| `99997`        | Triggers a **successful** payment callback. |
| `99999`        | Triggers a **declined** payment callback.   |

---
