# 📄 Payload for `payout-invoice` (Bank Transfer – Peru – PEN)

This document outlines the structure and required fields for the `payout-invoice` payload using the `bank_transfer_pen` service, which supports **bank transfers in Peru (PEN)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing or invalid, the request will be rejected.

---

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                                   |
| -------------- | ----------------------------------------------------------------------------- |
| `reference_id` | Unique identifier for the payout request (used for tracking and idempotency). |
| `service`      | Must be `"bank_transfer_pen"` for PEN bank transfer payouts.                  |
| `currency`     | Must be `"PEN"` (Peruvian Sol).                                               |
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

| JSON Key                  | Description                                                       |
| ------------------------- | ----------------------------------------------------------------- |
| `bank_code`               | Bank identifier code. Must match one of the supported bank codes. |
| `account_number`          | Bank account number of the beneficiary.                           |
| `account_type`            | Type of bank account.                                             |
| `document_type`           | Type of beneficiary document. Accepted value: `DNI`.              |
| `beneficiary_document_id` | Beneficiary document number (DNI).                                |

📝 **Important:**  
All keys listed above must be **nested under `fields`**.

---

## 🏦 Supported Bank Codes

The `bank_code` field must be sent as a **string** and must match one of the supported banks listed below.

| Code | Technical Name                               | Description                                  |
| ---- | -------------------------------------------- | -------------------------------------------- |
| 002  | Banco_de_credito_del_peru                    | Banco de Credito del Peru                    |
| 003  | Interbank                                    | Interbank                                    |
| 007  | Citibank                                     | Citibank                                     |
| 009  | Scotiabank                                   | Scotiabank                                   |
| 011  | Bbva_continental                             | BBVA Continental                             |
| 018  | Banco_de_la_nacion                           | Banco de la Nacion                           |
| 023  | Banco_de_comercio                            | Banco de Comercio                            |
| 035  | Banco_financiero                             | Banco Financiero                             |
| 038  | Banco_interamericano_de_finanzas             | Banco Interamericano de Finanzas             |
| 043  | Crediscotia_financiera                       | Crediscotia Financiera                       |
| 049  | Mi_banco                                     | Mi Banco                                     |
| 053  | Banco_gnb_peru_sa                            | Banco GNB Peru                               |
| 054  | Banco_falabella                              | Banco Falabella                              |
| 056  | Santander                                    | Santander                                    |
| 800  | Caja_metropolitana_de_lima                   | Caja Metropolitana de Lima                   |
| 801  | Caja_municipal_de_ahorro_y_credito_piura_sac | Caja Municipal de Ahorro y Credito Piura SAC |
| 802  | Caja_municipal_de_ahorro_y_credito_trujillo  | Caja Municipal de Ahorro y Credito Trujillo  |
| 803  | Caja_municipal_de_ahorro_y_credito_arequipa  | Caja Municipal de Ahorro y Credito Arequipa  |
| 805  | Caja_municipal_de_ahorro_y_credito_sullana   | Caja Municipal de Ahorro y Credito Sullana   |
| 806  | Caja_municipal_de_ahorro_y_credito_cuzco     | Caja Municipal de Ahorro y Credito Cuzco     |
| 808  | Caja_municipal_de_ahorro_y_credito_huancayo  | Caja Municipal de Ahorro y Credito Huancayo  |
| 809  | Cmac_ica                                     | CMAC Ica                                     |
| 922  | Dale                                         | Dale                                         |
| 099  | Financeira_confianza                         | Financeira Confianza                         |
| 096  | Financeira_efectiva                          | Financeira Efectiva                          |
| 094  | Financeira_oh                                | Financeira OH                                |
| 091  | Comportamos_financeira                       | Comportamos Financeira                       |
| 058  | Alfin_banco                                  | Alfin Banco                                  |
| 055  | Banco_ripley                                 | Banco Ripley                                 |
| 1005 | New_banco_de_credito                         | Banco de Credito                             |
| 1001 | New_bbva_continental                         | BBVA Continental                             |
| 1011 | New_interbank                                | Interbank                                    |
| 1006 | New_scotiabank_peru                          | Scotiabank Peru                              |
| 8442 | New_globokas_kasnet                          | Globokas Kasnet                              |
| 8510 | New_pago_efectivo                            | Pago Efectivo                                |
| 8320 | New_western_union                            | Western Union                                |
| 8443 | New_agente_niubiz                            | Agente Niubiz                                |
| 8444 | New_red_digital                              | Red Digital                                  |
| 8324 | New_caja_arequipa                            | Caja Arequipa                                |
| 8250 | New_caja_huancayo                            | Caja Huancayo                                |
| 1024 | New_caja_tacna                               | Caja Tacna                                   |
| 1025 | New_caja_trujillo                            | Caja Trujillo                                |
| 8391 | New_bcp_cuotatealo                           | BCP Cuotatealo                               |
| 8502 | New_pagoefectivo_qr                          | Pagoefectivo QR                              |
| 8621 | New_pagoefectivo_qr_dir                      | Pagoefectivo QR Dir                          |

---

## 🔍 Notes

- All amounts must be provided in **Peruvian Sol (PEN)**.
- `reference_id` must be unique per payout request.
- The `bank_code` must be sent as a **string**, even when numeric.
- Only banks listed in this document are supported.
- Invalid or unsupported bank codes will cause the request to fail.

---
