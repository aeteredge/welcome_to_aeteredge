# 📄 Payload for `payout-invoice` (Bank Transfer – Mexico – MXN)

This document outlines the structure and required fields for the `payout-invoice` payload using the `bank_transfer_mxn` service, which supports **bank transfers in Mexico (MXN)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing or invalid, the request will be rejected.

---

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                                   |
| -------------- | ----------------------------------------------------------------------------- |
| `reference_id` | Unique identifier for the payout request (used for tracking and idempotency). |
| `service`      | Must be `"bank_transfer_mxn"` for MXN bank transfer payouts.                  |
| `currency`     | Must be `"MXN"` (Mexican Peso).                                               |
| `amount`       | Amount to be paid out .                                                       |
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
| `account_number`            | Bank account number (CLABE).                                      |
| `account_type`              | Type of bank account.                                             |
| `beneficiary_document_type` | Type of beneficiary document. Accepted value: `CURP`.             |
| `beneficiary_document_id`   | Beneficiary CURP (18-character alphanumeric code).                |

📝 **Important:**  
All keys listed above must be **nested under `fields`**.

---

## 🏦 Supported Bank Codes

The `bank_code` field must be sent as a **string**, even when numeric, and must match one of the supported banks listed below.

| Code  | Technical Name  | Description     |
| ----- | --------------- | --------------- |
| 2001  | Banxico         | BANXICO         |
| 37006 | Bancomext       | BANCOMEXT       |
| 37009 | Banobras        | BANOBRAS        |
| 37019 | Banjercito      | BANJERCITO      |
| 37135 | Nafin           | NAFIN           |
| 37166 | Babien          | BaBien          |
| 37168 | Hipotecaria_fed | HIPOTECARIA FED |
| 40002 | Banamex         | BANAMEX         |
| 40012 | Bbva_mexico     | BBVA MEXICO     |
| 40014 | Santander       | SANTANDER       |
| 40021 | Hsbc            | HSBC            |
| 40030 | Bajio           | BAJIO           |
| 40036 | Inbursa         | INBURSA         |
| 40042 | Mifel           | MIFEL           |
| 40044 | Scotiabank      | SCOTIABANK      |
| 40058 | Banregio        | BANREGIO        |
| 40059 | Invex           | INVEX           |
| 40060 | Bansi           | BANSI           |
| 40062 | Afirme          | AFIRME          |
| 40072 | Banorte         | BANORTE         |
| 40106 | Bank_of_america | BANK OF AMERICA |
| 40108 | Mufg            | MUFG            |
| 40110 | Jp_morgan       | JP MORGAN       |
| 40112 | Bmonex          | BMONEX          |
| 40113 | Ve_por_mas      | VE POR MAS      |
| 40127 | Azteca          | AZTECA          |
| 40128 | Autofin         | AUTOFIN         |
| 40129 | Barclays        | BARCLAYS        |
| 40130 | Compartamos     | COMPARTAMOS     |
| 40132 | Multiva_banco   | MULTIVA BANCO   |
| 40133 | Actinver        | ACTINVER        |
| 40136 | Intercam_banco  | INTERCAM BANCO  |
| 40137 | Bancoppel       | BANCOPPEL       |
| 40138 | Uala            | UALA            |
| 40140 | Consubanco      | CONSUBANCO      |
| 40141 | Volkswagen      | VOLKSWAGEN      |
| 40143 | Cibanco         | CIBANCO         |
| 40145 | Bbase           | BBASE           |
| 40147 | Bankaool        | BANKAOOL        |
| 40148 | Pagatodo        | PAGATODO        |
| 40150 | Inmobiliario    | INMOBILIARIO    |
| 40151 | Donde           | DONDE           |
| 40152 | Bancrea         | BANCREA         |
| 40154 | Banco_covalto   | BANCO COVALTO   |
| 40155 | Icbc            | ICBC            |
| 40156 | Sabadell        | SABADELL        |
| 40157 | Shinhan         | SHINHAN         |
| 40158 | Mizuho_bank     | MIZUHO BANK     |
| 40159 | Bank_of_china   | BANK OF CHINA   |
| 40160 | Banco_s3        | BANCO S3        |
| 90600 | Monexcb         | MONEXCB         |
| 90601 | Gbm             | GBM             |
| 90602 | Masari          | MASARI          |
| 90605 | Value           | VALUE           |
| 90608 | Vector          | VECTOR          |
| 90616 | Finamex         | FINAMEX         |
| 90617 | Valmex          | VALMEX          |
| 90620 | Profuturo       | PROFUTURO       |
| 90630 | Cb_intercam     | CB INTERCAM     |
| 90631 | Ci_bolsa        | CI BOLSA        |
| 90634 | Fincomun        | FINCOMUN        |
| 90638 | Nu_mexico       | NU MEXICO       |
| 90642 | Reforma         | REFORMA         |
| 90646 | Stp             | STP             |
| 90652 | Credicapital    | CREDICAPITAL    |
| 90653 | Kuspit          | KUSPIT          |
| 90656 | Unagra          | UNAGRA          |
| 90659 | Asp_integra_opc | ASP INTEGRA OPC |
| 90661 | Alternativos    | ALTERNATIVOS    |
| 90670 | Libertad        | LIBERTAD        |
| 90677 | Caja_pop_mexica | CAJA POP MEXICA |
| 90680 | Cristobal_colon | CRISTOBAL COLON |
| 90683 | Caja_telefonist | CAJA TELEFONIST |
| 90684 | Transfer        | TRANSFER        |
| 90685 | Fondo_fira      | FONDO (FIRA)    |
| 90686 | Invercap        | INVERCAP        |
| 90689 | Fomped          | FOMPED          |
| 90699 | Fondeadora      | FONDEADORA      |
| 90703 | Tesored         | TESORED         |
| 90706 | Arcus           | ARCUS           |
| 90710 | Nvio            | NVIO            |
| 90722 | Mercado_pago_w  | Mercado Pago W  |
| 90723 | Cuenca          | CUENCA          |
| 90728 | Spin_by_oxxo    | SPIN BY OXXO    |
| 90902 | Indeval         | INDEVAL         |
| 90903 | Codi_valida     | CoDi Valida     |
| 97846 | Stp_test        |                 |

---

## 🔍 Notes

- All amounts must be provided in **Mexican Pesos (MXN)**.
- `reference_id` must be unique per payout request.
- The `bank_code` must be sent as a **string**, even when numeric.
- Only banks listed in this document are supported.
- Invalid or unsupported bank codes will cause the request to fail.

---
