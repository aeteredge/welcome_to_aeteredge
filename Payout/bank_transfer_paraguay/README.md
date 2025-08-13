# 📄 Payload for `payout-invoice` (Paraguay - PY)

This document outlines the structure and required fields for the `payout-invoice` payload using the `bank_transfer_pyg` service, which supports bank transfers in **Paraguay (PY)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be nested inside the fields object of the payload.
If any of them is missing or placed outside of fields, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                         |
| -------------- | ------------------------------------------------------------------- |
| `reference_id` | Unique identifier for the payout request (used for tracking).       |
| `service`      | Must be `"bank_transfer_pyg"` for Paraguay bank transfer payouts.   |
| `currency`     | Must be `"PYG"` for Paraguayan Guaraní.                             |
| `amount`       | Amount to be paid out (integer, no decimal places).                 |
| `test_mode`    | Set to `true` for test/sandbox mode, `false` for live transactions. |

---

### 🏦 Fields (nested under `fields`)

| JSON Key                    | Description                                                   |
| --------------------------- | ------------------------------------------------------------- |
| `bank_code`                 | Bank code (see the list below).                               |
| `account_type`              | Must be `"ACCOUNT_PARAGUAY"`.                                 |
| `bank_account`              | Beneficiary's bank account number.                            |
| `beneficiary_document_type` | Accepted values: `CI`, `PAS`, `CRP`, `CRC`, `RUC`, `DNI`.     |
| `beneficiary_document_id`   | Document number, Tax ID, or document code of the beneficiary. |
| `beneficiary_name`          | Full name of the beneficiary.                                 |
| `sender_full_name`          | Full name of the payer/sender.                                |

## 🏦 Bank Codes (`bank_code`)

Use one of the following codes as the value for `bank_code`:

| Code | Bank Name                                        |
| ---- | ------------------------------------------------ |
| 1    | BANCO CENTRAL DEL PARAGUAY                       |
| 2    | BANCO NACIONAL DE FOMENTO                        |
| 3    | BANCO DE LA NACION ARGENTINA                     |
| 4    | BANCO GNB PARAGUAY S.A.                          |
| 5    | BANCO DO BRASIL S.A.                             |
| 6    | CITIBANK N.A.                                    |
| 8    | SUDAMERIS BANK S.A.E.C.A.                        |
| 17   | BANCO ITAU PARAGUAY S.A.                         |
| 20   | BANCO CONTINENTAL S.A.                           |
| 30   | BANCO BASA (ex - Amambay)                        |
| 39   | VISION BANCO S.A.E.C.A.                          |
| 40   | BANCO RIO S.A.E.C.A. (Ex - Itapua)               |
| 41   | BANCO FAMILIAR S.A.E.C.A.                        |
| 42   | BANCO ATLAS                                      |
| 43   | BANCOP S.A.                                      |
| 44   | INTERFISA BANCO                                  |
| 6557 | FINANCIERA UENO S.A.E.C.A.                       |
| 6558 | CRISOL Y ENCARNACION FINANCIERA S.A.             |
| 6559 | FINLATINA S.A. DE FINANZAS                       |
| 6560 | FINANCIERA PARAGUAYO-JAPONESA S.A.E.C.A.         |
| 6561 | FINANCIERA EXPORTADORA PARAGUAYA S.A.            |
| 6564 | SOLAR S.A. DE AHORRO Y PRESTAMO PARA LA VIVIENDA |
| 6565 | TU FINANCIERA S.A.                               |
| 7079 | FIC S.A. DE FINANZAS                             |

💡 Make sure to use the correct bank code as listed to avoid processing errors.

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

- All amounts must be provided in **Guaraníes (PYG)** as integers.
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
