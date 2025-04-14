# 📄 Payload for `payout-invoice` (Colombia - CO)

This document outlines the structure and required fields for the `payout-invoice` payload using the `namebank_bank_cop` service, which supports **Bank transfers in Colombia (CO)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be nested inside the `fields` object of the payload.  
If any of them is missing or placed outside of `fields`, the request will be rejected.

| JSON Key              | Description                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| `bank_account_name`   | Name of the account holder.                                                 |
| `bank_account_number` | Account number associated with the bank.                                   |
| `identity_id`         | National ID or identity number of the beneficiary.                          |
| `id_type`             | Type of document. Accepted values: `CC`, `CE`, `PA`, `TI`, `RC`, `NIT`.     |
| `account_type`        | Type of account. Typically `"0"` for standard bank accounts.                |

📝 **Important:** These keys must be **nested under `fields`**

---

## 🏦 Supported Banks and Their Corresponding Services

To use one of the supported banks, set the corresponding `service` value in the payload:

| Bank Name                                        | Service Name                     |
|--------------------------------------------------|----------------------------------|
| Banco Itau                                       | `bancoitau_cop`                  |
| Banco Popular                                    | `bancopopular_cop`               |
| BBVA Colombia                                    | `bbva_colombia_cop`              |
| Banco de Bogota Desarrolllo 2013                 | `bogota_desarrollo_bank_cop`     |
| Citigroup Inc                                    | `citibank_colombia_cop`          |
| Bancolombia QA                                   | `colombia_bank_cop`              |
| Dale                                             | `dale_cop`                       |
| Banco Davivienda S.A.                            | `daviplata_cop`                  |
| Banco Davivienda                                 | `davivienda_bank_cop`            |
| Banco GNB Sudameris                              | `gnb_sudameris_bank_cop`         |
| Movii                                            | `movii_cop`                      |
| Banco de Occidente                               | `occidente_bank_cop`             |
| RappiPay Compañia de Financiamiento S.A          | `rappipay_cop`                   |
| Rappipay Daviplata                               | `rappipay_daviplata_cop`         |
| Scotiabank                                       | `scotiabank_cop`                 |

Make sure the correct `service` is selected based on the beneficiary's bank.

---

## 🔍 Notes

- `amount` must be provided in **Colombian Pesos (COP)** as an integer (no decimal places).
- `reference_id` is a unique identifier for the transaction (used for tracking).
- `test_mode: true` indicates this is a simulated transaction.
- Set `auto_process` to `true` or `false` to control whether the transaction is processed automatically. If set to `false`, you will need to approve it manually from the dashboard.
- Customer details (`reference_id`, `phone`, `email`, and `name`) must be provided inside the `customer` object.
- Additional metadata (e.g., `url`) must be included in the `metadata` object.

---

