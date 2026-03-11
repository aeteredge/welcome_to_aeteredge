# 📄 Payload for `payout-invoice` (Bank Transfer – Ecuador – USD)

This document outlines the structure and required fields for the `payout-invoice` payload using the `bank_transfer_usd` service, which supports **bank transfers in Ecuador (USD)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing or invalid, the request will be rejected.

---

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                                   |
| -------------- | ----------------------------------------------------------------------------- |
| `reference_id` | Unique identifier for the payout request (used for tracking and idempotency). |
| `service`      | Must be `"bank_transfer_usd"` for USD bank transfer payouts.                  |
| `currency`     | Must be `"USD"` (US Dollar).                                                  |
| `amount`       | Amount to be paid out.                                                        |
| `test_mode`    | Set to `true` for sandbox mode or `false` for live transactions.              |

---

### 👤 Customer (nested under `customer`)

| JSON Key       | Description                               |
| -------------- | ----------------------------------------- |
| `reference_id` | Unique identifier of the customer.        |
| `name`         | Full name of the customer or beneficiary. |
| `email`        | Email address of the customer.            |
| `phone`        | Customer phone number.                    |

---

### 🏦 Bank Fields (nested under `fields`)

| JSON Key                    | Description                                                       |
| --------------------------- | ----------------------------------------------------------------- |
| `account_number`            | Bank account number of the beneficiary.                           |
| `account_type`              | Type of bank account.                                             |
| `bank_code`                 | Bank identifier code. Must match one of the supported bank codes. |
| `beneficiary_document_id`   | Beneficiary document number.                                      |
| `beneficiary_document_type` | Type of beneficiary document. Accepted value: `CC`.               |

📝 **Important:**  
All keys listed above must be **nested under `fields`**.

---

## 🏦 Supported Bank Codes

The `bank_code` field must be sent as a **string** and must match one of the supported banks listed below.

| Code | Technical Name                   | Description                      |
| ---- | -------------------------------- | -------------------------------- |
| 0010 | Banco_pichincha                  | Banco Pichincha                  |
| 0017 | Banco_de_guayaquil_sa            | Banco de Guayaquil               |
| 0024 | Banco_city_bank                  | Banco City Bank                  |
| 0025 | Banco_machala                    | Banco Machala                    |
| 0201 | Banco_delbank_sa                 | Banco del Bank                   |
| 0029 | Banco_de_loja                    | Banco de Loja                    |
| 0030 | Banco_del_pacifico               | Banco del Pacifico               |
| 0032 | Banco_internacional              | Banco Internacional              |
| 0034 | Banco_amazonas                   | Banco Amazonas                   |
| 0035 | Banco_del_austro                 | Banco del Austro                 |
| 0036 | Banco_de_la_produccion_promerica | Banco de la Produccion Promerica |
| 0037 | Banco_bolivariano                | Banco Bolivariano                |
| 0039 | Banco_comercial_de_manabi        | Banco Comercial de Manabi        |
| 0042 | Banco_general_ruminahui          | Banco General Ruminahui          |
| 0043 | Banco_del_litoral_sa             | Banco del Litoral                |
| 0059 | Banco_solidario                  | Banco Solidario                  |
| 0060 | Banco_procredit_sa               | Banco Procredit                  |
| 0061 | Banco_capital_sa                 | Banco Capital                    |
| 0066 | Banecuador                       | Banecuador                       |

---

## 🔍 Notes

- All amounts must be provided in **US Dollars (USD)**.
- `reference_id` must be unique per payout request.
- The `bank_code` must be sent as a **string**, even when numeric.
- Invalid or unsupported bank codes will cause the request to fail.
