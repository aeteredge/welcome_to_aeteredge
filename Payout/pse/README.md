# 📄 Payload for `payout-invoice` (Colombia - COP)

This document outlines the structure and required fields for the `payout-invoice` payload using the `namebank_bank_cop` service, which supports **Bank transfers in Colombia (COP)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be nested inside the `fields` object of the payload.  
If any of them is missing or placed outside of `fields`, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                                          |
| -------------- | ------------------------------------------------------------------------------------ |
| `reference_id` | Unique identifier for the payout request (used for tracking).                        |
| `service`      | Must be set to the desired Colombian bank transfer service (e.g., `scotiabank_cop`). |
| `currency`     | Must be `"COP"` for Colombian Peso.                                                  |
| `amount`       | Amount to be paid out (integer, no decimal places).                                  |
| `test_mode`    | Set to `true` for sandbox mode, `false` for live transactions.                       |

---

### 🏦 Fields (nested under `fields`)

| JSON Key              | Description                                                             |
| --------------------- | ----------------------------------------------------------------------- |
| `bank_account_name`   | Name of the account holder.                                             |
| `bank_account_number` | Account number associated with the bank.                                |
| `identity_id`         | National ID or identity number of the beneficiary.                      |
| `id_type`             | Type of document. Accepted values: `CC`, `CE`, `PA`, `TI`, `RC`, `NIT`. |
| `account_type`        | Type of account. Typically `"0"` for standard bank accounts.            |

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

## 🏦 Supported Banks and Their Corresponding Services

To use one of the supported banks, set the corresponding `service` value in the payload:

| Bank Name                               | Service Name                 |
| --------------------------------------- | ---------------------------- |
| Banco Itau                              | `bancoitau_cop`              |
| Banco Popular                           | `bancopopular_cop`           |
| BBVA Colombia                           | `bbva_colombia_cop`          |
| Banco de Bogota Desarrolllo 2013        | `bogota_desarrollo_bank_cop` |
| Citigroup Inc                           | `citibank_colombia_cop`      |
| Bancolombia QA                          | `colombia_bank_cop`          |
| Dale                                    | `dale_cop`                   |
| Banco Davivienda S.A.                   | `daviplata_cop`              |
| Banco Davivienda                        | `davivienda_bank_cop`        |
| Banco GNB Sudameris                     | `gnb_sudameris_bank_cop`     |
| Movii                                   | `movii_cop`                  |
| Banco de Occidente                      | `occidente_bank_cop`         |
| RappiPay Compañia de Financiamiento S.A | `rappipay_cop`               |
| Rappipay Daviplata                      | `rappipay_daviplata_cop`     |
| Scotiabank                              | `scotiabank_cop`             |

Make sure the correct `service` is selected based on the beneficiary's bank.

---

## 🔍 Notes

- All amounts must be provided in **Colombian Pesos (COP)** as integers.
- `reference_id` must be unique for each payout.
- `test_mode: true` indicates the payout will be processed in sandbox mode.
- Customer information and metadata must be included as specified above.

---
