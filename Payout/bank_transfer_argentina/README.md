# 📄 Payload for `payout-invoice` (Bank Transfer – Argentina – ARS)

This document outlines the structure and required fields for the `payout-invoice` payload using the `bank_transfer_ars` service, which supports **bank transfers in Argentina (ARS)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing or invalid, the request will be rejected.

---

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                                   |
| -------------- | ----------------------------------------------------------------------------- |
| `reference_id` | Unique identifier for the payout request (used for tracking and idempotency). |
| `service`      | Must be `"bank_transfer_ars"` for ARS bank transfer payouts.                  |
| `currency`     | Must be `"ARS"` (Argentine Peso).                                             |
| `amount`       | Amount to be paid out.                                                        |
| `test_mode`    | Set to `true` for sandbox mode or `false` for live transactions.              |

---

### 👤 Customer (nested under `customer`)

| JSON Key       | Description                               |
| -------------- | ----------------------------------------- |
| `reference_id` | Unique identifier of the customer.        |
| `name`         | Full name of the customer or beneficiary. |

---

### 🏦 Bank Fields (nested under `fields`)

| JSON Key                    | Description                                                           |
| --------------------------- | --------------------------------------------------------------------- |
| `account_type`              | Type of bank account.                                                 |
| `bank_code`                 | Bank identifier code. Must match one of the supported bank codes.     |
| `beneficiary_document_type` | Type of beneficiary document. Accepted values: `DNI`, `CUIT`, `CUIL`. |
| `beneficiary_document_id`   | Beneficiary document number.                                          |
| `account_number`            | Bank account number of the beneficiary.                               |

📝 **Important:**  
All keys listed above must be **nested under `fields`**.

---

## 🏦 Supported Bank Codes

The `bank_code` field must be sent as a **string** and must match one of the supported banks listed below.

| Code | Technical Name               | Description                  |
| ---- | ---------------------------- | ---------------------------- |
| 7    | Banco_de_galicia             | Banco de Galicia             |
| 11   | Bando_de_la_nacion_argentina | Banco de la Nación Argentina |
| 14   | Banco_provincia_bsas         | Banco Provincia              |
| 15   | Icbc                         | ICBC                         |
| 16   | Citibank                     | CITIBANK                     |
| 17   | Bbva                         | BBVA                         |
| 20   | Banco_cordoba                | Banco Córdoba                |
| 27   | Superville                   | Superville                   |
| 29   | Banco_ciudad                 | Banco Ciudad                 |
| 34   | Patagonia                    | Patagonia                    |
| 44   | Hipotecario                  | Hipotecario                  |
| 45   | San_juan                     | San Juan                     |
| 65   | Municipal_rosario            | Municipal Rosario            |
| 72   | Santander                    | Santander                    |
| 83   | Chubut                       | Chubut                       |
| 86   | Santa_cruz                   | Santa Cruz                   |
| 93   | La_pampa                     | La Pampa                     |
| 94   | Corrientes                   | Corrientes                   |
| 97   | Neuquen                      | Neuquén                      |
| 143  | Brubank                      | Brubank                      |
| 147  | Interfinanzas                | Interfinanzas                |
| 150  | Hsbc                         | HSBC                         |
| 158  | Openbank                     | Openbank                     |
| 165  | Jpmorgan                     | JPMorgan                     |
| 191  | Credicoop                    | Credicoop                    |
| 259  | Itau                         | Itaú                         |
| 285  | Macro                        | Macro                        |
| 300  | Bice                         | BICE                         |
| 310  | Banco_del_sol                | Banco del Sol                |
| 336  | Bradesco                     | Bradesco                     |
| 384  | Wilobank                     | Wilobank                     |
| 415  | Rebanking                    | Rebanking                    |
| 515  | Bank_of_china                | Bank of China                |
| 000  | Cvu_account                  | CVU Account                  |

---

## 🔍 Notes

- All amounts must be provided in **Argentine Pesos (ARS)**.
- `reference_id` must be unique per payout request.
- The `bank_code` must be sent as a **string**, even when numeric.
- Only banks listed in this document are supported.
- Invalid or unsupported bank codes will cause the request to fail.
