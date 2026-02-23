# 📄 Payload for `payout-invoice` (Bank Transfer – Chile – CLP)

This document outlines the structure and required fields for the `payout-invoice` payload using the `bank_transfer_clp` service, which supports **bank transfers in Chile (CLP)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing or invalid, the request will be rejected.

---

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                                   |
| -------------- | ----------------------------------------------------------------------------- |
| `reference_id` | Unique identifier for the payout request (used for tracking and idempotency). |
| `service`      | Must be `"bank_transfer_clp"` for CLP bank transfer payouts.                  |
| `currency`     | Must be `"CLP"` (Chilean Peso).                                               |
| `amount`       | Amount to be paid out.                                                        |
| `test_mode`    | Set to `true` for sandbox mode or `false` for live transactions.              |

---

### 👤 Customer (nested under `customer`)

| JSON Key       | Description                               |
| -------------- | ----------------------------------------- |
| `reference_id` | Unique identifier of the customer.        |
| `name`         | Full name of the customer or beneficiary. |
| `email`        | Email address of the customer.            |

---

### 🏦 Bank Fields (nested under `fields`)

| JSON Key                    | Description                                                       |
| --------------------------- | ----------------------------------------------------------------- |
| `bank_code`                 | Bank identifier code. Must match one of the supported bank codes. |
| `account_number`            | Bank account number of the beneficiary.                           |
| `account_type`              | Type of bank account.                                             |
| `beneficiary_document_type` | Type of beneficiary document. .                                   |
| `beneficiary_document_id`   | Beneficiary document number .                                     |

📝 **Important:**  
All keys listed above must be **nested under `fields`**.

---

### ⚙️ Options (nested under `options`)

| JSON Key          | Description                                                                        |
| ----------------- | ---------------------------------------------------------------------------------- |
| `attempts_limit`  | Maximum number of payout attempts. `0` means unlimited attempts.                   |
| `split_mode`      | Enables or disables split payouts.                                                 |
| `allow_partially` | Allows partial payout processing when full amount cannot be completed.             |
| `auto_process`    | Set to `true` to automatically process the payout, or `false` for manual approval. |

---

## 🏦 Supported Bank Codes

The `bank_code` field must be sent as a **string** and must match one of the supported banks listed below.

| Code | Technical Name               | Description                  |
| ---- | ---------------------------- | ---------------------------- |
| 001  | Banco_de_chile               | Banco de Chile               |
| 009  | Banco_internacional          | Banco Internacional          |
| 012  | Banco_estado                 | Banco Estado                 |
| 014  | Scotiabank                   | Scotiabank                   |
| 016  | Bci                          | BCI                          |
| 028  | Banco_bice                   | Banco BICE                   |
| 031  | Hsbc_bank_chile              | HSBC Bank Chile              |
| 037  | Santander                    | Santander                    |
| 039  | Banco_itau                   | Banco Itaú                   |
| 049  | Banco_security               | Banco Security               |
| 051  | Banco_falabella              | Banco Falabella              |
| 053  | Banco_ripley                 | Banco Ripley                 |
| 055  | Banco_consorcio              | Banco Consorcio              |
| 504  | Banco_bbva                   | Banco BBVA                   |
| 729  | Caja_los_heroes              | Caja Los Héroes              |
| 672  | Coopeucht                    | Coopeucht                    |
| 732  | Los_andes                    | Los Andes                    |
| 875  | Mercado_pago                 | Mercado Pago                 |
| 730  | Tenpo                        | Tenpo                        |
| 017  | Banco_do_brasil              | Banco do Brasil              |
| 041  | Jp_morgan_chase_bank         | JP Morgan Chase Bank         |
| 043  | Banco_de_la_nacion_argentina | Banco de la Nación Argentina |
| 061  | Bank_of_china                | Bank of China                |
| 0059 | Banco_btg_pactual_chile      | Banco BTG Pactual Chile      |
| 0057 | Banco_paris                  | Banco Paris                  |
| 0056 | Banco_penta                  | Banco Penta                  |
| 0054 | Rabobank_chile               | Rabobank Chile               |

---

## 🔍 Notes

- All amounts must be provided in **Chilean Pesos (CLP)**.
- `reference_id` must be unique per payout request.
- The `bank_code` must be sent as a **string**, even when numeric.
- Only banks listed in this document are supported.
- Invalid or unsupported bank codes will cause the request to fail.
